```
normalize_position(pos, model::ABM{<:Union{AbstractGridSpace,ContinuousSpace}})
```

Return the position `pos` normalized for the extents of the space of the given `model`. For periodic spaces, this wraps the position along each dimension, while for non-periodic spaces this clamps the position to the space extent.
