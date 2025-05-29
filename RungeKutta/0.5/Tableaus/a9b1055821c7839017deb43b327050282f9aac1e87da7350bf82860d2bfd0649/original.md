Tableau of Runge's two-stage, 2nd order method

```julia
TableauRunge(::Type{T}=Float64) where {T}
```

The constructor takes one optional argument, that is the element type of the tableau.

Reference:

```
Carl Runge
Über die numerische Auflösung von Differentialgleichungen.
Mathematische Annalen, Volume 46, Pages 167-178, 1895.
doi: 10.1007/BF01446807.
Equation (3)
```
