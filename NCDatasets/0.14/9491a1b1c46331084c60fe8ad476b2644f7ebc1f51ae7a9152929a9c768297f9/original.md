```
defDim(ds::NCDataset,name,len)
```

Define a dimension in the data set `ds` with the given `name` and length `len`. If `len` is the special value `Inf`, then the dimension is considered as `unlimited`, i.e. it will grow as data is added to the NetCDF file.

For example:

```julia
using NCDatasets
ds = NCDataset("/tmp/test.nc","c")
defDim(ds,"lon",100)
# [...]
close(ds)
```

This defines the dimension `lon` with the size 100.

To create a variable with an unlimited dimensions use for example:

```julia
using NCDatasets
ds = NCDataset("/tmp/test2.nc","c")
defDim(ds,"lon",10)
defDim(ds,"lat",10)
defDim(ds,"time",Inf)
defVar(ds,"unlimited_variable",Float64,("lon","lat","time"))
@show ds.dim["time"]
# returns 0 as no data is added
ds["unlimited_variable"][:,:,1:4] = randn(10,10,4)
@show ds.dim["time"]
# returns now 4 as 4 time slice have been added
close(ds)
```
