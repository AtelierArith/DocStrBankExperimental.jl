```
pseudoabsencemask(::Type{WithinRadius}, presences::SDMLayer{Bool}; distance::Number = 100.0, )
```

Generates a mask for pseudo-absences where pseudo-absences can be within a `distance` (in kilometers) of the original observation. Internally, this uses `DistanceToEvent`.
