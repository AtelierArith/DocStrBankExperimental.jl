```
cheb_filter_matrix(weights::AbstractVector{TF}, S::AbstractMatrix{TF}, A::AbstractMatrix{TF}; negsum::Bool=true) where TF<:AbstractFloat
```

Construct a filter matrix using precomputed weights and operators for Chebyshev collocation methods, optionally applying the 'negative sum trick', which seems make the simulation more stable according to my tests.

# Arguments

  * `weights`: Vector of filter weights
  * `S`: Chebyshev synthesis matrix: maps Chebyshev series to function values at Chebyshev grid points
  * `A`: Chebyshev analysis matrix: maps function values at Chebyshev grid points to Chebyshev series
  * `negative_sum_trick`: Boolean flag for negative sum trick (default: true)

The function applies the weights through diagonal scaling and implements the negative sum trick for diagonal elements when `negative_sum_trick` is true.
