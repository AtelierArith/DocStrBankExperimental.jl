```
interpolate([T=ComplexF64,] nep::NEP, intpoints::Array)
```

Interpolates a NEP in the points `intpoints` and returns a [`PEP`](@ref), i.e., a polynomial eigenvalue problem in a monomial basis. See [`ChebPEP`](@ref) for Chebyshev interpolation. The optional argument `T` is the type in which the matrices of the PEP should be defined.

See also [`ChebPEP`](@ref).
