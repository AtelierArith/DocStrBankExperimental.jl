```
nearby_ids(pos, model::ABM, r = 1; kwargs...) → ids
```

Return an iterable over the IDs of the agents within distance `r` (inclusive) from the given position. The position must match type with the spatial structure of the `model`. The specification of what "distance" means depends on the space, hence it is explained in each space's documentation string. Keyword arguments are space-specific and also described in each space's documentation string.

`nearby_ids` always includes IDs with 0 distance to `pos`.
