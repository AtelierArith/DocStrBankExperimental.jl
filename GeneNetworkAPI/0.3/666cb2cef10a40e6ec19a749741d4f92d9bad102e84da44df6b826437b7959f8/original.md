```
download_pheno(dataset::String;gn_url::String=gn_url())
```

Downloads the non-omic ("clinical") phenotypes for a given `dataset`. The file will be downloaded in `path` location, if  `path` is not specified, then  the file will be a temporary file.
