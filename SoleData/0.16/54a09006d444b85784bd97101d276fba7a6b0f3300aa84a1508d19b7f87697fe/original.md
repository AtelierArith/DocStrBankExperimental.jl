```
struct VariableValue{I<:VariableId, N<:Union{VariableName, Nothing}} <: AbstractUnivariateFeature
    i_variable::I
    i_name::N
end
```

A simple feature, equal the value of a scalar variable and, optionally, its name.

See also [`SoleLogics.Interval`](@ref), [`SoleLogics.Interval2D`](@ref), [`AbstractUnivariateFeature`](@ref), [`VarFeature`](@ref), [`AbstractFeature`](@ref).
