```
ControlBoundConstraint{P,M,T}
```

Linear bound constraint on controls

# Constructors

```julia
ControlBoundConstraint(m; u_min, u_max)
```

Any of the bounds can be ±∞. The bound can also be specifed as a single scalar, which applies the bound to all controls.
