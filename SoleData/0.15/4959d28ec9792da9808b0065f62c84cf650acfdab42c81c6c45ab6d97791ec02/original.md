```
struct VariableValue{I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
end
```

A simple feature, equal the value of a scalar variable.

See also [`SoleLogics.Interval`](@ref), [`SoleLogics.Interval2D`](@ref), [`AbstractUnivariateFeature`](@ref), [`VarFeature`](@ref), [`AbstractFeature`](@ref).
