```
CompiledSystem <: AbstractSystem
```

An [`AbstractSystem`](@ref) which automatically compiles a straight line program for the fast evaluation of a system `F` and its Jacobian. For large systems the compilation can take some time and require a large amount of memory. If this is a problem consider [`InterpretedSystem`](@ref).

```
CompiledSystem(F::System)
```

Construct a `CompiledSystem` from the given [`System`](@ref) `F`.
