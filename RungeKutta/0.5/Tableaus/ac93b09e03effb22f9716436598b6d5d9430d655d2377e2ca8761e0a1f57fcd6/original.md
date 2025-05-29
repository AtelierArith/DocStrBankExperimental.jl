Gauss tableau with s stages

```julia
TableauGauss(::Type{T}, s)
TableauGauss(s) = TableauGauss(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

References:

```
John C. Butcher.
Implicit Runge-Kutta processes.
Mathematics of Computation, Volume 18, Pages 50-64, 1964.
doi: 10.1090/S0025-5718-1964-0159424-9.

John C. Butcher.
Gauss Methods. 
In: Engquist B. (eds). Encyclopedia of Applied and Computational Mathematics. Springer, Berlin, Heidelberg. 2015.
doi: 10.1007/978-3-540-70529-1_115.
```
