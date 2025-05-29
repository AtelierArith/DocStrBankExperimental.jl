```julia
struct ChemEquation{T<:Real}
```

  * `tuples::Array{Tuple{ChemEquations.Compound, T}, 1} where T<:Real`

Stores chemical equation's compounds and their coefficients in a structured way.
