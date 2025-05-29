```
alignment(alignment_result)
```

Return the alignment if any as a [`PairwiseAlignment`](@ref). To get the [`Alignment`](@ref), nest the function, e.g. `alignment(alignment(alignment_result))`. This function returns a `PairwiseAlignment` instead of an `Alignment` for backwards-compatibility reasons.

See also: `hasalignment`
