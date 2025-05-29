```
∫(expr::JuMP.AbstractJuMPScalar,
  prefs::AbstractArray{GeneralVariableRef},
  [lower_bounds::Union{Real, AbstractArray{<:Real}} = NaN,
  upper_bounds::Union{Real, AbstractArray{<:Real}} = NaN;
  kwargs...])::GeneralVariableRef
```

A convenient wrapper for [`integral`](@ref). The unicode symbol `∫` is produced  via `\int`.
