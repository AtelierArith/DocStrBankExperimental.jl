```
isomorphism([T::Type=Float64,] codomain::TensorSpace, domain::TensorSpace) -> TensorMap
isomorphism([T::Type=Float64,] codomain ← domain) -> TensorMap
isomorphism([T::Type=Float64,] domain → codomain) -> TensorMap
isomorphism!(t::AbstractTensorMap) -> AbstractTensorMap
```

Construct a specific isomorphism between the codomain and the domain, i.e. return a `t::TensorMap` where either `scalartype(t) = T` if `T` is a `Number` type or `storagetype(t) = T` if `T` is a `DenseVector` type. If the spaces are not isomorphic, an error will be thrown.

!!! note
    There is no canonical choice for a specific isomorphism, but the current choice is such that `isomorphism(cod, dom) == inv(isomorphism(dom, cod))`.


See also [`unitary`](@ref) when `InnerProductStyle(cod) === EuclideanInnerProduct()`.
