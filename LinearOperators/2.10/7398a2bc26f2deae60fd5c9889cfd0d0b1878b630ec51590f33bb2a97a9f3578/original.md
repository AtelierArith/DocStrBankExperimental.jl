```
DiagonalAndrei(d)
```

Construct a linear operator that represents a diagonal quasi-Newton approximation as described in

Andrei, N. A diagonal quasi-Newton updating method for unconstrained optimization. https://doi.org/10.1007/s11075-018-0562-7

The approximation satisfies the weak secant equation and is not guaranteed to be positive definite.

# Arguments

  * `d::AbstractVector`: initial diagonal approximation.
