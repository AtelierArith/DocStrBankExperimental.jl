```julia
struct FunctionLayer{__T_nodes, __T_skip} <: LuxCore.AbstractLuxWrapperLayer{:nodes}
```

A container for multiple [`DecisionNodes`](@ref).  It accumulates all outputs of the nodes.

# Fields

  * `nodes`
  * `skip`
