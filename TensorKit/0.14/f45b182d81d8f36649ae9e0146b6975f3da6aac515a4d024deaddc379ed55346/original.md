```
unitary([T::Type=Float64,] codomain::TensorSpace, domain::TensorSpace) -> TensorMap
unitary([T::Type=Float64,] codomain ← domain) -> TensorMap
unitary([T::Type=Float64,] domain → codomain) -> TensorMap
unitary!(t::AbstractTensorMap) -> AbstractTensorMap
```

Construct a specific unitary morphism between the codomain and the domain, i.e. return a `t::TensorMap` where either `scalartype(t) = T` if `T` is a `Number` type or `storagetype(t) = T` if `T` is a `DenseVector` type. If the spaces are not isomorphic, or the spacetype does not have a Euclidean inner product, an error will be thrown.

!!! note
    There is no canonical choice for a specific unitary, but the current choice is such that `unitary(cod, dom) == inv(unitary(dom, cod)) = adjoint(unitary(dom, cod))`.


See also [`isomorphism`](@ref) and [`isometry`](@ref).
