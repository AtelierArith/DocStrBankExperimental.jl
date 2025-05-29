```
distance_to_set(distance_definition, v, s)
```

Compute the distance of a value to a set. When `v ∈ s`, the distance is zero (or all individual distances are zero).

Each set `S` implements at least `distance_to_set(d::DefaultDistance, v::T, s::S)` with `T` of appropriate type for members of the set.
