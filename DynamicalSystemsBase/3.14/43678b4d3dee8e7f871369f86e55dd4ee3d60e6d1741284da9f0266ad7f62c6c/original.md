```
set_state!(ds::DynamicalSystem, value::Real, i) → u
```

Set the `i`th variable of `ds` to `value`. The index `i` can be an integer or a symbolic-like index for systems that reference a ModelingToolkit.jl model. For example:

```julia
i = :x # or `1` or `only(@variables(x))`
set_state!(ds, 0.5, i)
```

**Warning:** this function should not be used with derivative dynamical systems such as Poincare/stroboscopic/projected dynamical systems. Use the method below to manipulate an array and give that to `set_state!`.

```
set_state!(u::AbstractArray, value, index, ds::DynamicalSystem)
```

Modify the given state `u` and leave `ds` untouched.
