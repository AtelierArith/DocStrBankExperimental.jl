```
getindex(a::Attributes,name::SymbolOrString)
```

Return the value of the attribute called `name` from the attribute list `a`. Generally the attributes are loaded by indexing, for example:

```julia
using NCDatasets
ds = NCDataset("file.nc")
title = ds.attrib["title"]
```
