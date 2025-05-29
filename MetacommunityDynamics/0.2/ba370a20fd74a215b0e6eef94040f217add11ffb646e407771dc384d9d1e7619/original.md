```
Coordinates(layer::E; coords = [(rand(), rand()) for _ = 1:20]) where E<:EnvironmentLayer
```

Builds a `Coordinates` where the environmental variable is built from a single EnvironmentLayer, and optionally the set of coordinates can be passed as a keyword argument.
