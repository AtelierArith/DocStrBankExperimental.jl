```
projection_on_set(distance_definition, v, s)
```

Compute the projection of a vector `v` on a set `s`.

Each set `S` implements at least `projection_on_set(d::DefaultDistance, v::T, s::S)` with `T` of appropriate type for members of the set.
