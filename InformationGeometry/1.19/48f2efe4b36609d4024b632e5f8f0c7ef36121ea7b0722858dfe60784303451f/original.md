```
ValidationProfiles(DM::AbstractDataModel, yComp::Int, Ts::AbstractVector; Confnum::Real=2, dof::Int=DOF(DM), OffsetToZero::Bool=false, kwargs...)
```

Computes a set of validation profiles for the component `yComp` of the prediction at various values of the independent variables `Ts`. The uncertainty of the ficticious validation data point can be optionally chosen via the keyword argument `σv`. Most other kwargs are passed on to the `ParameterProfiles` function and thereby also to the optimizers, see e.g. [`ParameterProfiles`](@ref), [`InformationGeometry.minimize`](@ref).
