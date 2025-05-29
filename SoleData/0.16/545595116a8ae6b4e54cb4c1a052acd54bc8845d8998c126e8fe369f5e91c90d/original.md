```
struct UnivariateNamedFeature{U<:Real,I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
    name::VariableName
end
```

A univariate feature solely identified by its name and reference variable.

See also [`SoleLogics.Interval`](@ref), [`SoleLogics.Interval2D`](@ref), [`AbstractUnivariateFeature`](@ref), [`VarFeature`](@ref), [`AbstractFeature`](@ref).
