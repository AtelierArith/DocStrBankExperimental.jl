```
NormConstraint{S,D,T}
```

Constraint of the form $\|y\|_2 \leq a$ where $y$ is made up of elements from the state and/or control vectors. The can be equality constraint, e.g. $y^T y - a^2 = 0$, an inequality constraint, where `y^T y - a^2 \leq 0`, or a second-order constraint.

# Constructor:

```
NormConstraint(n, m, a, sense, [inds])
```

where `n` is the number of states,     `m` is the number of controls,     `a` is the constant on the right-hand side of the equation,     `sense` is `Inequality()`, `Equality()`, or `SecondOrderCone()`, and     `inds` can be a `UnitRange`, `AbstractVector{Int}`, or either `:state` or `:control`

# Examples:

```julia
NormConstraint(3, 2, 4, Equality(), :control)
```

creates a constraint equivalent to $\|u\|^2 = 16.0$ for a problem with 2 controls.

```julia
NormConstraint(3, 2, 3, Inequality(), :state)
```

creates a constraint equivalent to $\|x\|^2 \leq 9$ for a problem with 3 states.

```julia
NormConstraint(3, 2, 5, SecondOrderCone(), :control)
```

creates a constraint equivalent to  $\|x\|_2 \leq 5$.
