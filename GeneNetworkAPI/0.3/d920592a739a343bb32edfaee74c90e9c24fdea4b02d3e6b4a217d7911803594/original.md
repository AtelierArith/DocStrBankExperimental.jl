```
list_geno(group::String; gn_url::String=gn_url())
```

Returns a data frame with the location name of the different geno files of  a group, and if available some metadata such as strain of the first filial generation, maternal and paternal strain.  If there exist more than one location, the default location is indicated  by a `*`. 
