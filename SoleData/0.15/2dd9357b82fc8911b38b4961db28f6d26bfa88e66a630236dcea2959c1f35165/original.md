```
struct VariableSoftMin{T<:AbstractFloat,I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
    alpha::T
end
```

Univariate feature computing a "softened" version of the minimum value for a given variable.

See also [`SoleLogics.Interval`](@ref), [`SoleLogics.Interval2D`](@ref), [`AbstractUnivariateFeature`](@ref), [`VariableMin`](@ref), [`VarFeature`](@ref), [`AbstractFeature`](@ref).
