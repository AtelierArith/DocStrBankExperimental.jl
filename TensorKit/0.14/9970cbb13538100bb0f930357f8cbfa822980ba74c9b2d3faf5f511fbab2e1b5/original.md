```
DiagonalTensorMap{T}(undef, domain::S) where {T,S<:IndexSpace}
# expert mode: select storage type `A`
DiagonalTensorMap{T,S,A}(undef, domain::S) where {T,S<:IndexSpace,A<:DenseVector{T}}
```

Construct a `DiagonalTensorMap` with uninitialized data.
