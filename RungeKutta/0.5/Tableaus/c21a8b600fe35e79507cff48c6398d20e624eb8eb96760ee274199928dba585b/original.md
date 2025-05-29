Tableau of Crank-Nicolson two-stage, 2nd order method

```julia
TableauCrankNicolson(::Type{T}=Float64) where {T}
```

The constructor takes one optional argument, that is the element type of the tableau.

Reference:

```
J. Crank and P. Nicolson.
A practical method for numerical evaluation of solutions of partial differential equations of the heat-conduction type.
Mathematical Proceedings of the Cambridge Philosophical Society, Volume 43, Issue 1, Pages 50-67, 1947.
doi: 10.1017/S0305004100023197
```
