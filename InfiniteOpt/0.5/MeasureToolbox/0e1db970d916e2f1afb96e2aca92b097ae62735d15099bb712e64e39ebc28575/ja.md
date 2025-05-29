```
∫(expr::JuMP.AbstractJuMPScalar,
  prefs::AbstractArray{GeneralVariableRef},
  [lower_bounds::Union{Real, AbstractArray{<:Real}} = NaN,
  upper_bounds::Union{Real, AbstractArray{<:Real}} = NaN;
  kwargs...])::GeneralVariableRef
```

[`integral`](@ref) の便利なラッパーです。ユニコードシンボル `∫` は `\int` を介して生成されます。
