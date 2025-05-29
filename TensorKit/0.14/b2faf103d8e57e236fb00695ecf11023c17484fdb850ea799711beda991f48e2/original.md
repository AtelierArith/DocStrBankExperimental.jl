```
isometry([T::Type=Float64,] codomain::TensorSpace, domain::TensorSpace) -> TensorMap
isometry([T::Type=Float64,] codomain ← domain) -> TensorMap
isometry([T::Type=Float64,] domain → codomain) -> TensorMap
isometry!(t::AbstractTensorMap) -> AbstractTensorMap
```

Construct a specific isometry between the codomain and the domain, i.e. return a `t::TensorMap` where either `scalartype(t) = T` if `T` is a `Number` type or `storagetype(t) = T` if `T` is a `DenseVector` type. The isometry `t` then satisfies `t' * t = id(domain)` and `(t * t')^2 = t * t'`. If the spaces do not allow for such an  isometric inclusion, an error will be thrown.

See also [`isomorphism`](@ref) and [`unitary`](@ref).
