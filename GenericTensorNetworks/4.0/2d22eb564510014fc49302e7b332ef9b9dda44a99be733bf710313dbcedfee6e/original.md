```
SingleConfigMin{K, BOUNDED} <: AbstractProperty
SingleConfigMin(k::Int; bounded=false)
```

Finding single solution with smallest-K size.

  * The corresponding data type is inverted [`CountingTropical{Float64,<:ConfigSampler}`](@ref) if `BOUNDED` is `false`, inverted [`Tropical`](@ref) otherwise.
  * Weighted constraint satisfaction problems is supported.
  * GPU is supported,

## Keyword Arguments

  * `bounded`, if it is true, use bounding trick (or boolean gradients) to reduce the working memory to store intermediate configurations.
