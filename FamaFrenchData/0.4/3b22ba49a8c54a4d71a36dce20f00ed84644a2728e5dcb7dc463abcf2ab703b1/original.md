```
listFamaFrench(;refresh=false)
```

Returns a vector of possible table names. Reads from `listFamaFrench.txt`. When `refresh = true`, first crawls the website to find current list of tables, then overwrites `listFamaFrench.txt` with this list. The selection of tables is rarely changed, so the provided list is likely sufficient.
