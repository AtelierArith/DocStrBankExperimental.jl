```
modes_sub(ℳ::Vector{<:TransmissionMode}, str::String)
modes_sub(ℳ::Vector{<:TransmissionMode}, str_arr::Array{String})
```

Returns an array containing all [`TransmissionMode`](@ref)s that include in the name the String `str` or any of values in the String array `str_arr`.
