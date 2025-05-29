```julia
rebuildFactorMetadata!(dfg, factor; ...)
rebuildFactorMetadata!(
    dfg,
    factor,
    neighbors;
    _blockRecursionGradients
)

```

After deserializing a factor using decodePackedType, use this to completely rebuild the factor's CCW and user data.

Notes:

  * This function is likely to be used for cache heavy factors, e.g. `ObjectAffordanceSubcloud`.

Dev Notes:

  * TODO: We should only really do this in-memory if we can by without it (review this).
  * TODO: needs testing
