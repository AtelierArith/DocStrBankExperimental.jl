```
ECCOdiags_add(nam::String)
```

Add data to the scratch space folder. Known options for `nam` include  "release1", "release2", "release3", "release4", "release5", and "OCCA2HR1".

Under the hood this is the same as:

```
using Climatology
datadep"ECCO4R1-stdiags"
datadep"ECCO4R2-stdiags"
datadep"ECCO4R3-stdiags"
datadep"ECCO4R4-stdiags"
datadep"ECCO4R5-stdiags"
datadep"OCCA2HR1-stdiags"
```
