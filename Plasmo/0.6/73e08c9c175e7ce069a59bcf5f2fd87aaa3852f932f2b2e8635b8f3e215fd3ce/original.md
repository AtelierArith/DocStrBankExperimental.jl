```
OptiNode{GT<:AbstractOptiGraph} <: AbstractOptiNode
```

A data structure meant to encapsulate variables, constraints, an objective function, and  other model data. An optinode is "lightweight" in the sense that it does not directly  contain model data, but instead acts as an interface that maps to a backend where  the model data is stored. This avoids the need to generate memory overhead through  container structures in cases when a node contains very little model data.
