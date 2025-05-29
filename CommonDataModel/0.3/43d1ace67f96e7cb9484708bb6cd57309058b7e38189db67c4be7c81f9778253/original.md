```
setindex!(d::Dimensions,len,name::AbstractString)
```

Defines the dimension called `name` to the length `len`, for example:

```julia
ds = NCDataset("file.nc","c")
ds.dim["longitude"] = 100
```

If `len` is the special value `Inf`, then the dimension is considered as `unlimited`, i.e. it will grow as data is added to the NetCDF file.
