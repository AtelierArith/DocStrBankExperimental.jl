Tableau of symmetric and symplectic three-stage, 4th order Runge-Kutta method

```julia
TableauSRK3(::Type{T}=Float64) where {T}
```

The constructor takes one optional argument, that is the element type of the tableau.

Reference:

```
Shan Zhao and Guo-Wei Wei.
A unified discontinuous Galerkin framework for time integration.
Mathematical Methods in the Applied Sciences, Volume 37, Issue 7, Pages 1042-1071, 2014.
doi: 10.1002/mma.2863.
```
