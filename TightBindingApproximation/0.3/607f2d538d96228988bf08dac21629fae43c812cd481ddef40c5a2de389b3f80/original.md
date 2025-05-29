```
BerryCurvatureData{R<:ReciprocalSpace, C<:Array{Float64}, N<:Union{Vector{Float64}, Float64, Nothing}} <: Data
```

Data of Berry curvature, including:

1. `reciprocalspace::R`: reciprocal space on which the Berry curvature is computed.
2. `values::C`: Berry curvature for a certain set of bands.
3. `chernnumber::N`: if not `nothing`, Chern number of each energy band when it is a vector or total Chern number of all bands when it is a number.
