```
download_geno(group::String,format::String="geno";
                gn_url::String=gn_url(),
                path::String = "")
```

Download the genotype matrix for a `group` in a given `format`.

Currently works only for files in the `geno` format.

The file will be downloaded in `path` location, if  `path` is not specified, then  the file will be a temporary file.
