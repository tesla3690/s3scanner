# s3enum
AWS S3 Bucket/Object Finder

```
   _____ ____        ____             _        _          ______                       
 / ____|___ \      |  _ \           | |      | |        |  ____|                      
| (___   __) |_____| |_) |_   _  ___| | _____| |_ ______| |__   _ __  _   _ _ __ ___  
 \___ \ |__ <______|  _ <| | | |/ __| |/ / _ \ __|______|  __| | '_ \| | | | '_ ` _ \ 
 ____) |___) |     | |_) | |_| | (__|   <  __/ |_       | |____| | | | |_| | | | | | |
|_____/|____/      |____/ \__,_|\___|_|\_\___|\__|      |______|_| |_|\__,_|_| |_| |_|
                                                                                      

  AWS S3 Bucket Finder
  


usage: s3enum.py [-h] [-w wordlist] [-n root] [-o] [-a] [-p] [-b batch]

AWS s3 Bucket Permutation Checker

optional arguments:
  -h, --help   show this help message and exit
  -w wordlist  Specify list of buckets to check from wordlist
  -n root      Specify the root name to use, i.e. google, amazon
  -o           Check objects in a public s3 bucket if they are available
  -a           Use AWS Credentials to authenticate the request
  -p           Only show buckets/objects that are public in the results
  -b batch     Specify filename containing words to apply permutations to
```

## How To Use

You can either use a pre-made wordlist containing all the buckets/objects you want to check or supply a root name, and let s3enum add in common permutations to the bucket name to find different variations. 

### Example

If you wanted to look for any information for `example`, you'd run `python s3enum.py -n example`, you can supply the argument `-o` if you want to check the status of the objects contained in the public buckets.

```
    _____ ____        ____             _        _          ______                       
 / ____|___ \      |  _ \           | |      | |        |  ____|                      
| (___   __) |_____| |_) |_   _  ___| | _____| |_ ______| |__   _ __  _   _ _ __ ___  
 \___ \ |__ <______|  _ <| | | |/ __| |/ / _ \ __|______|  __| | '_ \| | | | '_ ` _ \ 
 ____) |___) |     | |_) | |_| | (__|   <  __/ |_       | |____| | | | |_| | | | | | |
|_____/|____/      |____/ \__,_|\___|_|\_\___|\__|      |______|_| |_|\__,_|_| |_| |_|
                                                                                      
         

  AWS S3 Bucket Finder



[!] Applying permutations to example
[!] Bucket is marked private [http://example-dev.s3.amazon
.com]
[>] Bucket has a redirect [http://s3.amazonaws.com/example-dev] Redirected here - [example-dev.s3.amazonaws.com]
[-] Bucket does not exist or cannot list [http://example-prod.s3.amazonaws.com]
[-] Bucket does not exist or cannot list [http://s3.amazonaws.com/example-prod]
[-] Bucket does not exist or cannot list [http://example-production.s3.amazonaws.com]
[-] Bucket does not exist or cannot list [http://s3.amazonaws.com/example-production]
[-] Bucket does not exist or cannot list [http://example-tmp.s3.amazonaws.com]
[-] Bucket does not exist or cannot list [http://s3.amazonaws.com/example-tmp]
[!] Bucket is marked private [http://example-media.s3.amazonaws.com]
[>] Bucket has a redirect [http://s3.amazonaws.com/example-media] Redirected here - [example-media.s3.amazonaws.com]
[-] Bucket does not exist or cannot list [http://example-tmp-logs.s3.amazonaws.com]
[-] Bucket does not exist or cannot list [http://s3.amazonaws.com/example-tmp-logs]
[!] Bucket is marked private [http://example-logs.s3.amazonaws.com]
[!] Bucket is marked private [http://s3.amazonaws.com/example-logs]
[-] Bucket does not exist or cannot list [http://example-splunk.s3.amazonaws.com]
[-] Bucket does not exist or cannot list [http://s3.amazonaws.com/example-splunk]```


If you want to do lookups on a batch of companies, you can specify `-b` and supply a wordlist file, with a name on each line. The tool will then run through each line and lookup each name along with the list of permutations consecutively. I would recommend specifying `-p` to only output the public buckets/objects.

## TODO
- Right now, the AWS credentials are hardcoded in the python script, which should be handled through the `/.aws` credential file.
