```
eigvals(tba::Union{TBA, Algorithm{<:TBA}}, k::Union{AbstractVector{<:Number}, Nothing}=nothing; options...) -> Vector{<:Number}
eigvals(tba::Union{TBA, Algorithm{<:TBA}}, reciprocalspace::ReciprocalSpace; options...) -> Vector{<:Vector{<:Number}}
```

Get the eigen values of a free quantum lattice system.
