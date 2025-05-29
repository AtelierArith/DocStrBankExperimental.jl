```
eigvecs(tba::Union{TBA, Algorithm{<:TBA}}, k::Union{AbstractVector{<:Number}, Nothing}=nothing; options...) -> Matrix{<:Number}
eigvecs(tba::Union{TBA, Algorithm{<:TBA}}, reciprocalspace::ReciprocalSpace; options...) -> Vector{<:Matrix{<:Number}}
```

Get the eigen vectors of a free quantum lattice system.
