```
nonlinearity(f)
nonlinearity(T, f)
```

Create a pure nonlinearity. `f` is assumed to be a static (no memory) nonlinear function from $f : R -> R$.

The type `T` defaults to `Float64`.

NOTE: The nonlinear functionality in ControlSystemsBase.jl is currently experimental and subject to breaking changes not respecting semantic versioning. Use at your own risk.

# Example:

Create a LTI system with a static input nonlinearity that saturates the input to [-1,1].

```julia
tf(1, [1, 1])*nonlinearity(x->clamp(x, -1, 1))
```

See also predefined nonlinearities [`saturation`](@ref), [`offset`](@ref).

Note: when composing linear systems with nonlinearities, it's often important to handle operating points correctly. See [`ControlSystemsBase.offset`](@ref) for handling operating points.
