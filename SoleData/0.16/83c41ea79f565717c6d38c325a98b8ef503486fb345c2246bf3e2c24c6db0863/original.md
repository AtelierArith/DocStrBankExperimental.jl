```
struct VariableMax{I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
end
```

Notable univariate feature computing the maximum value for a given variable.

See also [`SoleLogics.Interval`](@ref), [`SoleLogics.Interval2D`](@ref), [`AbstractUnivariateFeature`](@ref), [`VariableMin`](@ref), [`VarFeature`](@ref), [`AbstractFeature`](@ref).
