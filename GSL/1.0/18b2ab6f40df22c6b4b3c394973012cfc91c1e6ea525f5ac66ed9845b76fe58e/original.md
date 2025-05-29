```
wrap_gsl_matrix(m::Ptr{gsl_matrix}) -> Array{Float64,2}
```

Return a Julia matrix wrapping the data of a gsl_matrix

**REMEMBER** that GSL stores matrices in row-major, so matrix will be transposed.
