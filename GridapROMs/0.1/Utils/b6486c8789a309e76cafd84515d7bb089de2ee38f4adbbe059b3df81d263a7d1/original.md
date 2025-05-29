```
compute_error(
  sol::AbstractArray{T,N},
  sol_approx::AbstractArray{T,N},
  args...
  ) where {T,N} -> Number
```

Computes the error between `sol` and `sol_approx`, by default in the Euclidean norm. A different norm (usually represented by a sparse matrix) can be provided as an argument.
