```
ftnswrite(filename, tns)
```

Write a sparse Finch tensor to a FROSTT `.tns` file.

[TensorMarket](https://github.com/willow-ahrens/TensorMarket.jl) must be loaded for this function to be available.

!!! danger
    This file format does not record the size or eltype of the tensor, and is provided for archival purposes only.


See also: [tnswrite](http://willowahrens.io/TensorMarket.jl/stable/#TensorMarket.tnswrite)
