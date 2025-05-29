```
modes_sub(l::Transmission, str::String)
modes_sub(l::Transmission, string_array::Array{String})
modes_sub(ℒᵗʳᵃⁿˢ::Vector{<:Transmission}, str::String)
modes_sub(ℒᵗʳᵃⁿˢ::Vector{<:Transmission}, string_array::Array{String})
```

Returns an array containing all [`TransmissionMode`](@ref)s of [`Transmission`])@ref) corridor `l` or in a vector of transmission corridors `ℒᵗʳᵃⁿˢ` that include in the name the String `str` or any of values in the String array `str_arr`.
