```
StateBoundConstraint{P,N,T}
```

Linear bound constraint on states

# Constructors

```julia
StateBoundConstraint(n; x_min, x_max)
```

Any of the bounds can be ±∞. The bound can also be specifed as a single scalar, which applies the bound to all states.
