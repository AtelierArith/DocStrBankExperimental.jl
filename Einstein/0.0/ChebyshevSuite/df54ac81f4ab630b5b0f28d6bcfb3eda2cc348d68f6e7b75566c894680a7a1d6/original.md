```
cheb_series_filter_weights_exp([TF=Float64], n::Integer, a::Integer, p::Integer) where {TF<:AbstractFloat}
```

Compute exponential filter weights for Chebyshev series [Szilagyi:2009qz](@cite).

$$
w_k = e^{-\alpha\left(k / n\right)^{2 p}}, \quad k = 0, \ldots, n-1
$$

# Arguments

  * `TF`: Type parameter for floating-point precision
  * `n`: Number of grid points
  * `α`: Filter strength parameter
  * `p`: Order of filter

# Examples

  * $$
    \alpha = 36
    $$

    and $p = 32$ for weak filter [Szilagyi:2009qz, Hilditch:2015aba](@cite)
  * $$
    \alpha = 40
    $$

    and $p = 8$ for strong filter [justin*ripley*2023_8215577](@cite)
