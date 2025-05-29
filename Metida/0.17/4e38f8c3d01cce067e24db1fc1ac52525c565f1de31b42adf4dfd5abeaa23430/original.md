```
fit(::Type{T}, f::FormulaTerm, data;
contrasts=Dict{Symbol,Any}(),  
random::Union{Nothing, VarEffect, Vector{VarEffect}} = nothing, 
repeated::Union{Nothing, VarEffect} = nothing,
kwargs...)
```

Fit LMM model with @formula.

Keywords see [`fit!`](@ref)
