```
OptiEdge{GT<:AbstractOptiGraph} <: AbstractOptiEdge
```

A data structure meant to encapsulate linking constraints and other model data. An optiedge  is "lightweight" in the sense that it does not directly contain model data, but instead acts as an interface that maps to a backend where the model data is stored. This avoids the need  to generate memory overhead through container structures in cases when a node contains very  little model data.
