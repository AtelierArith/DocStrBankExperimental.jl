```
InterpretedHomotopy <: AbstractHomotopy
```

An [`AbstractHomotopy`](@ref) which automatically generates a program for the fast evaluation of `H` and its Jacobian. The program is however, not compiled but rather interpreted. See also [`CompiledHomotopy`](@ref).

```
InterpretedHomotopy(H::Homotopy)
```

Construct an `InterpretedHomotopy` from the given [`Homotopy`](@ref) `H`.
