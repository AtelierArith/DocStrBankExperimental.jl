```julia
struct LayeredDAG{__T_layers} <: LuxCore.AbstractLuxWrapperLayer{:layers}
```

A container for a layered directed acyclic graph consisting of different [`DecisionLayer`](@ref)s.

# Fields

  * `layers`
