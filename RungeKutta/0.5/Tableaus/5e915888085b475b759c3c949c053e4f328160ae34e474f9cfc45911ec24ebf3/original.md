Tableau of explicit Runge-Kutta method of order four with four stages

```julia
TableauRK42(::Type{T}=Float64) where {T}
```

The constructor takes one optional argument, that is the element type of the tableau.

Reference:

```
John C. Butcher
Numerical Methods for Ordinary Differential Equations. Wiley, 2016.
Page 102
```
