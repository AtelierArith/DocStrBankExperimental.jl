```
pauliy([T=ComplexF64,] b::NLevelBasis)
```

Generalized Pauli $Y$ operator for the given `N` level system.

Returns `Y^pow = ω^pow X^pow Z^pow` where `ω = ω = exp(2π*1im*pow/N)` and `N = length(b)` when odd or `N = 2*length(b)` when even. This is due to the  order of the generalized Pauli group in even versus odd dimensions.

See [`paulix`](@ref) and [`pauliz`](@ref) for more details.
