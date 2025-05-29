```
download_omics(dataset::String; 
                gn_url::String=gn_url(), 
                path::String = tempname())
```

Download the omic phenotypes for a given `dataset`. The file will be downloaded in `path` location, if  `path` is not specified, then  the file will be a temporary file.
