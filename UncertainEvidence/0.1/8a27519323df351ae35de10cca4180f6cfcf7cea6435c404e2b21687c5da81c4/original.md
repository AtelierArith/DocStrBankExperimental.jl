```
BPA = Dict{T,S} where {T<:Any, S<:Real}
```

A basic probability assessment (BPA) is the foundational data structure for calculations in the context of the Dempster-Shafer theory (DST).

Use `bpa` to create automatically normalized BPAs. Otherwise, use `redistribute!` for normalization.

See also: [`bpa`](@ref), [`redistribute!`](@ref).
