```
SingleConfigMax{K, BOUNDED} <: AbstractProperty
SingleConfigMax(k::Int; bounded=false)
```

Finding single solution for largest-K sizes, e.g. for [`IndependentSet`](@ref) problem, it is one of the maximum independent sets.

  * The corresponding data type is [`CountingTropical{Float64,<:ConfigSampler}`](@ref) if `BOUNDED` is `false`, [`Tropical`](@ref) otherwise.
  * Weighted constraint satisfaction problems is supported.
  * GPU is supported,

## Keyword Arguments

  * `bounded`, if it is true, use bounding trick (or boolean gradients) to reduce the working memory to store intermediate configurations.
