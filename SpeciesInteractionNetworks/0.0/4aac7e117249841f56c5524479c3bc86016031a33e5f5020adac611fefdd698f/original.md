```
render(::Type{Quantitative{T}}, N::SpeciesInteractionNetwork{<:Partiteness, <:Interactions}) where {T <: Number}
```

Returns a quantitative version of the network, where interaction strengths have the type `T`. This can be used to convert a quantitative network into a different number representation.
