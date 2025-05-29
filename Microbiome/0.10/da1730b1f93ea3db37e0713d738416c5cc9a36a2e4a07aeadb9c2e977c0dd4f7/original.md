```
hasrank(gf::GeneFunction)::Bool
```

Boolean function that returns:

  * `true` if `gf` has a [`Taxon`](@ref) with a non-missing `rank` field,
  * `false` if there's no `Taxon`, or
  * `false` if the `Taxon` has no `rank`
