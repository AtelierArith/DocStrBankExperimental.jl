```
extract_attractors(mapper::AttractorsMapper) → attractors
```

Return a dictionary mapping label IDs to attractors found by the `mapper`. This function should be called after calling [`basins_fractions`](@ref) with the given `mapper` so that the attractors have actually been found first.

For `AttractorsViaFeaturizing`, the attractors are only stored if the mapper was called with pre-defined initial conditions rather than a sampler (function returning initial conditions).
