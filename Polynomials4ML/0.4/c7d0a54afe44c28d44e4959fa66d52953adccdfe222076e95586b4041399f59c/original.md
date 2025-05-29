`function orthpolybasis(...)` : construct a univariate orthogonal polynomial  basis with respect to some specified inner product. For the standard 3-term  recursion polynomials, use `legendre_basis`, `jacobi_basis` or `chebyshev_basis`. 

The `orthpolybasis` currently implements orthogonal polynomials for discrete weights with the following constructors: 

```julia
orthpolybasis(N::Integer, W::DiscreteWeights{TW}; TX = Float64)
orthpolybasis(N::Integer, X::AbstractVector{<: Real}, 
              W::AbstractVector{<: Real}, normalizeW=false; kwargs...)
```
