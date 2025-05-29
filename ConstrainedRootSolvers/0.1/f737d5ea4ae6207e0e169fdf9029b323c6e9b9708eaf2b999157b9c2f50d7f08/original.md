This method uses residual tolerance and Nelder-Mead method, also known as     simplex method:

```
find_peak(f::Function,
          ms::NelderMeadMethod{FT},
          tol::ResidualTolerance{FT};
          stepping::Bool = false
) where {FT<:AbstractFloat}
```

Find the solution, given

  * `f` A function to solve
  * `ms` [`NelderMeadMethod`](@ref) type method struct
  * `tol` [`ResidualTolerance`](@ref) type tolerance struct
  * `stepping` Optional. If true, save the optimization steps to the history   field in method struct.
