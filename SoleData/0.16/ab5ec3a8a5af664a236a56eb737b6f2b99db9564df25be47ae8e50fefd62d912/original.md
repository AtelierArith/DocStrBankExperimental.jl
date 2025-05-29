```
struct VariableMin{I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
end
```

Notable univariate feature computing the minimum value for a given variable.

See also [`SoleLogics.Interval`](@ref), [`SoleLogics.Interval2D`](@ref), [`AbstractUnivariateFeature`](@ref), [`VariableMax`](@ref), [`VarFeature`](@ref), [`AbstractFeature`](@ref).
