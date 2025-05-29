```
norm(v::CeedVector, p::Real)
```

Return the norm of the given [`CeedVector`](@ref), see [`norm(::CeedVector, ::NormType)`](@ref).

`p` can have value 1, 2, or Inf, corresponding to `NORM_1`, `NORM_2`, and `NORM_MAX`, respectively.
