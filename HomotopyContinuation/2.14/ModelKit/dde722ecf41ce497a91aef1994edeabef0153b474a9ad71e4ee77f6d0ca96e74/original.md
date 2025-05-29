```
InterpretedSystem <: AbstractSystem
```

An [`AbstractSystem`](@ref) which automatically generates a program for the fast evaluation of `F` and its Jacobian. The program is however, not compiled but rather interpreted. See also [`CompiledSystem`](@ref).

```
InterpretedSystem(F::System)
```

Construct an `InterpretedSystem` from the given [`System`](@ref) `F`.
