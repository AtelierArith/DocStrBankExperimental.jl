```
struct UnivariateFeature{U,I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
    f::Function
    fname::Union{Nothing,String}
end
```

A dimensional feature represented by the application of a generic function `f` to a single variable of a dimensional channel. For example, it can wrap a scalar function computing how much red a `Interval2D` world, when interpreted on an image, contains. Optionally, a feature name `fname` can be attached to the function, which can be useful for inspection (e.g., if `f` is an anonymous function, this avoids names such s "#47" or "#49".

See also [`SoleLogics.Interval`](@ref), [`SoleLogics.Interval2D`](@ref), [`AbstractUnivariateFeature`](@ref), [`VarFeature`](@ref), [`AbstractFeature`](@ref).
