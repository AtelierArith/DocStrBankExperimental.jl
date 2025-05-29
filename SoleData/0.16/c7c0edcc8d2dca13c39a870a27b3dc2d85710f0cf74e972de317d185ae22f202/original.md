```
struct VariableSoftMax{T<:AbstractFloat,I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
    alpha::T
end
```

Univariate feature computing a "softened" version of the maximum value for a given variable.

See also [`SoleLogics.Interval`](@ref), [`SoleLogics.Interval2D`](@ref), [`AbstractUnivariateFeature`](@ref), [`VariableMax`](@ref), [`VarFeature`](@ref), [`AbstractFeature`](@ref).
