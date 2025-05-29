```
gaussCoeffOf(b::FloatingGTBasisFuncs{T}) -> Matrix{T}
```

Return the exponent and contraction coefficients of each [`GaussFunc`](@ref) (in each row  of the returned `Matrix`) inside `b`.
