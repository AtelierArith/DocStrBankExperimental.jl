```
ftnsread(filename)
```

Read the contents of the FROSTT `.tns` file 'filename' into a Finch COO Tensor.

[TensorMarket](https://github.com/willow-ahrens/TensorMarket.jl) must be loaded for this function to be available.

!!! danger
    This file format does not record the size or eltype of the tensor, and is provided for archival purposes only.


See also: [tnsread](http://willowahrens.io/TensorMarket.jl/stable/#TensorMarket.tnsread)
