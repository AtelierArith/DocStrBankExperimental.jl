```
get_pedigree(pedfile::AbstractString;header=false,separator=',',missingstrings=["0"])
```

  * Get pedigree informtion from a pedigree file with **header** (defaulting to `false`) , **separator** (defaulting to `,`) and missing values (defaulting to ["0"])
  * Pedigree file format:

```
a,0,0
c,a,b
d,a,c
```
