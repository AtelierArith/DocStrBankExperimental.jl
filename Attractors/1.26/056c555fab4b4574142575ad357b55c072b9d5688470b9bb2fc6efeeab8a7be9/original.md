```
matching_map(b₊::AbstractArray, b₋::AbstractArray, matcher::MatchByBasinOverlap)
```

Special case of `matching_map` where instead of having as input dictionaries mapping IDs to values, we have `Array`s which represent basins of attraction and whose elements are the IDs.

See [`MatchByBasinOverlap`](@ref) for how matching works.
