```
IDMatcher
```

Supertype of all "matchers" that match can IDs labelling attractors. Currently available matchers:

  * [`MatchBySSSetDistance`](@ref)
  * [`MatchByBasinEnclosure`](@ref)
  * [`MatchByBasinOverlap`](@ref)

Matchers implement an extendable interface based on the function [`matching_map`](@ref). This function is used by the higher level function [`match_sequentially!`](@ref), which can be called after any call to a global continuation to match attractors differently, if the matching used originally during the continuation was not the best.
