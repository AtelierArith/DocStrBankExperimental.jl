```
dae_index_lowering(sys::ODESystem; kwargs...) -> ODESystem
```

Perform the Pantelides algorithm to transform a higher index DAE to an index 1 DAE. `kwargs` are forwarded to [`pantelides!`](@ref). End users are encouraged to call [`structural_simplify`](@ref) instead, which calls this function internally.
