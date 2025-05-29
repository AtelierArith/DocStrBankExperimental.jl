```
symmap_to_varmap(sys, symmap)
```

Given a system and map of `Symbol`s to values, generates a map from corresponding symbolic variables/parameters to the values that can be used to pass initial conditions and parameter mappings.

For example,

```julia
sir = @reaction_network sir begin
    β, S + I --> 2I
    ν, I --> R
end
subsys = @reaction_network subsys begin
    k, A --> B
end
@named sys = compose(sir, [subsys])
```

gives

```
Model sys with 3 equations
Unknowns (5):
  S(t)
  I(t)
  R(t)
  subsys₊A(t)
  subsys₊B(t)
Parameters (3):
  β
  ν
  subsys₊k
```

to specify initial condition and parameter mappings from *symbols* we can use

```julia
symmap = [:S => 1.0, :I => 1.0, :R => 1.0, :subsys₊A => 1.0, :subsys₊B => 1.0]
u0map  = symmap_to_varmap(sys, symmap)
pmap   = symmap_to_varmap(sys, [:β => 1.0, :ν => 1.0, :subsys₊k => 1.0])
```

`u0map` and `pmap` can then be used as input to various problem types.

Notes:

  * Any `Symbol`, `sym`, within `symmap` must be a valid field of `sys`. i.e. `sys.sym` must be defined.
