```
CompiledHomotopy <: AbstractHomotopy
```

An [`AbstractHomotopy`](@ref) which automatically compiles a straight line program for the fast evaluation of a homotopy `H` and its Jacobian. For large homotopies the compilation can take some time and require a large amount of memory. If this is a problem consider [`InterpretedHomotopy`](@ref).

```
CompiledSystem(F::System)
```

Construct a `CompiledSystem` from the given [`System`](@ref) `F`.
