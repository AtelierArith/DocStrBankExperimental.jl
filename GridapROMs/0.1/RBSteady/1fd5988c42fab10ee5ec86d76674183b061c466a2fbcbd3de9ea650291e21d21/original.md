```
abstract type Reduction{A<:ReductionStyle,B<:NormStyle} end
```

Type indicating the reduction strategy to employ, and the information regarding the norm with respect to which the reduction should occur.

Subtypes:

  * [`DirectReduction`](@ref)
  * [`GreedyReduction`](@ref)
  * [`SupremizerReduction`](@ref)
  * [`AbstractMDEIMReduction`](@ref)
  * [`TransientReduction`](@ref)
