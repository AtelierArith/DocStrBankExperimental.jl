Tableau of explicit Runge-Kutta method of order five with six stages

```julia
TableauRK5(::Type{T}=Float64) where {T}
```

The constructor takes one optional argument, that is the element type of the tableau.

Reference:

```
John C. Butcher
Numerical Methods for Ordinary Differential Equations. Wiley, 2016.
Page 103
```
