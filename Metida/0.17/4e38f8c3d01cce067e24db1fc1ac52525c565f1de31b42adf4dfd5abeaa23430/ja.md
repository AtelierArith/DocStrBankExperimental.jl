```
fit(::Type{T}, f::FormulaTerm, data;
contrasts=Dict{Symbol,Any}(),  
random::Union{Nothing, VarEffect, Vector{VarEffect}} = nothing, 
repeated::Union{Nothing, VarEffect} = nothing,
kwargs...)
```

@formulaを使用してLMMモデルをフィットします。

キーワードは[`fit!`](@ref)を参照してください。
