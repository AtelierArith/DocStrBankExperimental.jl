```
decompose(bf::CompositeGTBasisFuncs{T, D}, splitGaussFunc::Bool=false) -> 
Matrix{<:BasisFunc{T, D}}
```

Decompose a `CompositeGTBasisFuncs` into a `Matrix` of [`BasisFunc`](@ref)s. The sum of  each column represents one orbital of the input basis function(s). If `splitGaussFunc` is  `true`, then each column consists of the `BasisFunc`s with only 1 [`GaussFunc`](@ref).
