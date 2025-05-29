```
add_datadep(nam::String)
```

Add data to the scratch space folder. Known options for `nam` include  "release1", "release2", "release3", "release4", "release5", and "OCCA2HR1".

Under the hood this is the same as:

```
using Climatology
add_datadep("IPCC")
```
