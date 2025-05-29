```
ShuffleDimensions()
```

Multidimensional surrogates of input `StateSpaceSet`s from StateSpaceSets.jl. Each point in the set is individually shuffled, but the points themselves are not shuffled.

These surrogates destroy the state space structure of the dataset and are thus suited to distinguish deterministic datasets from high dimensional noise.
