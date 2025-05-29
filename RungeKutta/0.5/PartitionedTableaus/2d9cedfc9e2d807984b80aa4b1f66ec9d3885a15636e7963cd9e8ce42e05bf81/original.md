Partitioned Gauss-Legendre Runge-Kutta tableau with s stages

```julia
PartitionedTableauGauss(::Type{T}, s)
PartitionedTableauGauss(s) = PartitionedTableauGauss(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

This [`PartitionedTableau`](@ref) uses [`TableauGauss`](@ref) for both coefficients `a` and `ā`.
