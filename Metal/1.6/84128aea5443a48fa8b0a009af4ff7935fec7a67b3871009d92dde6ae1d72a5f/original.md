```
MtlArray{T,N,S} <: AbstractGPUArray{T,N}
```

`N`-dimensional Metal array with storage mode `S` and elements of type `T`.

`S` can be `Metal.PrivateStorage` (default), `Metal.SharedStorage`, or `Metal.ManagedStorage`.

See the Array Programming section of the Metal.jl docs for more details.
