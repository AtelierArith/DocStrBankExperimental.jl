```
∫(expr::JuMP.AbstractJuMPScalar,
  pref::GeneralVariableRef,
  [lower_bound::Real = NaN,
  upper_bound::Real = NaN;
  kwargs...])::GeneralVariableRef
```

[`integral`](@ref) の便利なラッパーです。`∫` のユニコードシンボルは `\int` を介して生成されます。
