This method uses [`BisectionMethod`](@ref) method:

```
find_zero(f::Function,
          ms::BisectionMethod{FT},
          tol::Union{ResidualTolerance{FT}, SolutionTolerance{FT}};
          stepping::Bool = false
) where {FT<:AbstractFloat}
```

Returns the solution where target function is zero, given

  * `f` Function to solve
  * `ms` [`BisectionMethod`](@ref) type method struct
  * `tol` [`ResidualTolerance`](@ref) or [`SolutionTolerance`](@ref) type   tolerance struct
  * `stepping` Optional. If true, save the optimization steps to the history   field in method struct.
