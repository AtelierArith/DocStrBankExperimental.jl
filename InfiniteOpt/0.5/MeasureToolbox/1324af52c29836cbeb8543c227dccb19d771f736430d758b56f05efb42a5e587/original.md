```
@∫(expr::JuMP.AbstractJuMPScalar,
   prefs::Union{GeneralVariableRef, AbstractArray{GeneralVariableRef}},
   [lower_bounds::Union{Real, AbstractArray{<:Real}} = default_bounds,
   upper_bounds::Union{Real, AbstractArray{<:Real}} = default_bounds;
   kwargs...])::GeneralVariableRef
```

A convenient wrapper for [`@integral`](@ref). The unicode symbol `∫` is produced  via `\int`.
