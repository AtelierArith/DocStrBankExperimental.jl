```
manhattan_distance(a, b, model::ABM)
```

Return the manhattan distance between `a` and `b` (either agents or agent positions), respecting periodic boundary conditions (if in use). Works with any space where it makes sense: currently `AbstractGridSpace` and `ContinuousSpace`.
