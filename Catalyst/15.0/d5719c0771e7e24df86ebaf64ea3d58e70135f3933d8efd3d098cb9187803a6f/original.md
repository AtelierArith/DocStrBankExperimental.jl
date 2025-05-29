```
reactioncomplexmap(rn::ReactionSystem)
```

Find each [`ReactionComplex`](@ref) within the specified system, constructing a mapping from the complex to vectors that indicate which reactions it appears in as substrates and products.

Notes:

  * Each [`ReactionComplex`](@ref) is mapped to a vector of pairs, with each pair having the form `reactionidx => ± 1`, where `-1` indicates the complex appears as a substrate and `+1` as a product in the reaction with integer label `reactionidx`.
  * Constant species are ignored as part of a complex. i.e. if species `A` is constant then the reaction `A + B --> C + D` is considered to consist of the complexes `B` and `C + D`. Likewise `A --> B` would be treated as the same as `0 --> B`.
