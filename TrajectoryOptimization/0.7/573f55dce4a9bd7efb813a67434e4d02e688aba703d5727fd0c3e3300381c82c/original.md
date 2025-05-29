```
GoalConstraint{P,T}
```

Constraint of the form $x_g = a$, where $x_g$ can be only part of the state vector.

# Constructors:

```julia
GoalConstraint(xf::AbstractVector)
GoalConstraint(xf::AbstractVector, inds)
```

where `xf` is an n-dimensional goal state. If `inds` is provided, only `xf[inds]` will be used.
