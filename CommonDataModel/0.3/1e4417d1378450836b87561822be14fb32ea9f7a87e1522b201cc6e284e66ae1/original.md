```
Base.setindex!(a::Attributes,data,name::SymbolOrString)
```

Set the attribute called `name` to the value `data` in the attribute list `a`. `data` can be a vector or a scalar. A scalar is handeld as a vector with one element in the NetCDF data model.

Generally the attributes are defined by indexing, for example:

```julia
ds = NCDataset("file.nc","c")
ds.attrib["title"] = "my title"
close(ds)
```
