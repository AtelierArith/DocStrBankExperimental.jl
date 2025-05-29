```
Coordinates(layers::Vector{E}; coords = [(rand(), rand()) for _ = 1:20]) where E<:EnvironmentLayer
```

Builds a coordinate set with environmental variables passed as a vector of EnvironmentLayers, and optionally coordinates passed as a keyword argument. 
