Tableau of Ralston's two-stage, 2nd order method

```julia
TableauRalston2(::Type{T}=Float64) where {T}
```

The constructor takes one optional argument, that is the element type of the tableau.

Reference:

```
Anthony Ralston.
Runge-Kutta Methods with Minimum Error Bounds.
Mathematics of Computation, Volume 16, Pages 431-437, 1962.
doi: 10.1090/S0025-5718-1962-0150954-0.
Equation (3.5)
```
