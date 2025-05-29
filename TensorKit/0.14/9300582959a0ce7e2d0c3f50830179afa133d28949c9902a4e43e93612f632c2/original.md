```
id([T::Type=Float64,] V::TensorSpace) -> TensorMap
id!(t::AbstractTensorMap) -> AbstractTensorMap
```

Construct the identity endomorphism on space `V`, i.e. return a `t::TensorMap` with `domain(t) == codomain(t) == V`, where either `scalartype(t) = T` if `T` is a `Number` type or `storagetype(t) = T` if `T` is a `DenseVector` type.

See also [`one!`](@ref).
