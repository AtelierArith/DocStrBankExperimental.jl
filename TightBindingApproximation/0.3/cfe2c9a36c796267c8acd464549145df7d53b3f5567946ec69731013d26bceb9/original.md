```
eigen(tba::Union{TBA, Algorithm{<:TBA}}, k::Union{AbstractVector{<:Number}, Nothing}=nothing; options...) -> Eigen
eigen(tba::Union{TBA, Algorithm{<:TBA}}, reciprocalspace::ReciprocalSpace; options...) -> Tuple{Vector{<:Vector{<:Number}}, Vector{<:Matrix{<:Number}}}
```

Get the eigen values and eigen vectors of a free quantum lattice system.
