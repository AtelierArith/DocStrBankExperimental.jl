```
BoundConstraint{P,NM,T}
```

Linear bound constraint on states and controls

# Constructors

```julia
BoundConstraint(n, m; x_min, x_max, u_min, u_max)
```

Any of the bounds can be ±∞. The bound can also be specifed as a single scalar, which applies the bound to all state/controls.
