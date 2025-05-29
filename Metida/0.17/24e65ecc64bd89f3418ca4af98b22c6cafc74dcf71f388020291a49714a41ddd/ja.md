```
fit(::Type{T}, f::LMMformula, data;
contrasts=Dict{Symbol,Any}(),  
kwargs...) where T <: LMM
```

[`@lmmformula`](@ref)を使用してLMMモデルをフィットします。

キーワードは[`fit!`](@ref)を参照してください。
