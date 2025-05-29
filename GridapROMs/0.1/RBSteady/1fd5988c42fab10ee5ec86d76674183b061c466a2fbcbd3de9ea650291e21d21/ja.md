```
abstract type Reduction{A<:ReductionStyle,B<:NormStyle} end
```

削減戦略を示す型と、削減が行われるべきノルムに関する情報。

サブタイプ:

  * [`DirectReduction`](@ref)
  * [`GreedyReduction`](@ref)
  * [`SupremizerReduction`](@ref)
  * [`AbstractMDEIMReduction`](@ref)
  * [`TransientReduction`](@ref)
