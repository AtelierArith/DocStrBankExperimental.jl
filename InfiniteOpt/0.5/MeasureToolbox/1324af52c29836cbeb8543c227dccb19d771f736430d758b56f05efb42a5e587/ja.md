```
@∫(expr::JuMP.AbstractJuMPScalar,
   prefs::Union{GeneralVariableRef, AbstractArray{GeneralVariableRef}},
   [lower_bounds::Union{Real, AbstractArray{<:Real}} = default_bounds,
   upper_bounds::Union{Real, AbstractArray{<:Real}} = default_bounds;
   kwargs...])::GeneralVariableRef
```

[`@integral`](@ref) の便利なラッパーです。ユニコードシンボル `∫` は `\int` を介して生成されます。
