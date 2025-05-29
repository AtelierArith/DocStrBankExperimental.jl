```
fit(::Type{T}, f::LMMformula, data;
contrasts=Dict{Symbol,Any}(),  
kwargs...) where T <: LMM
```

Fit LMM model with [`@lmmformula`](@ref).

Keywords see [`fit!`](@ref)
