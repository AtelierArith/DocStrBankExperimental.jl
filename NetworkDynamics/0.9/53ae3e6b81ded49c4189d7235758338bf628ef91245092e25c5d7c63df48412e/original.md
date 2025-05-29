```
ff_to_constraint(v::VertexModel)
```

Takes `VertexModel` `v` with feed forward and turns all algebraic output states into internal states by defining algebraic constraints contraints `0 = out - g(...)`. The new output function is just a [`StateMask`](@ref) into the extended internal state vector.

Returns the transformed `VertexModel`.
