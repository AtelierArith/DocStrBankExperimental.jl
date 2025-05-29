```
struct MultivariateFeature{U} <: VarFeature
    f::Function
end
```

A dimensional feature represented by the application of a function to a dimensional channel. For example, it can wrap a scalar function computing how much a `Interval2D` world, when interpreted on an image, resembles a horse. Note that the image has a number of spatial variables (3, for the case of RGB), and "resembling a horse" may require a computation involving all variables.

See also [`SoleLogics.Interval`](@ref), [`SoleLogics.Interval2D`](@ref), [`AbstractUnivariateFeature`](@ref), [`VarFeature`](@ref), [`AbstractFeature`](@ref).
