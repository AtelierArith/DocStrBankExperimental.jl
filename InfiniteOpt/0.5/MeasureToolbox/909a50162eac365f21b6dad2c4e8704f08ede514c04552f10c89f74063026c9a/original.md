```
∫(expr::JuMP.AbstractJuMPScalar,
  pref::GeneralVariableRef,
  [lower_bound::Real = NaN,
  upper_bound::Real = NaN;
  kwargs...])::GeneralVariableRef
```

A convenient wrapper for [`integral`](@ref). The `∫` unicode symbol is produced  via `\int`.
