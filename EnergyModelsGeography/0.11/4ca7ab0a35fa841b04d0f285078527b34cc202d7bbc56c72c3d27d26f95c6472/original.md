```
modes_sub(l::Transmission, p::Resource)
modes_sub(ℒᵗʳᵃⁿˢ::Vector{<:Transmission}, p::Resource)
```

Returns an array containing all [`TransmissionMode`](@ref)s that transport the resource `p` in [`Transmission`])@ref) corridor `l` or in a vector of transmission corridors `ℒᵗʳᵃⁿˢ`.
