```
QKData{T<:Real,N}
```

A data structure for holding an `M x T_bar` array of real values (`Y`) plus two integer fields (`M`, `T_bar`) derived from its dimensions. `M` is  the dimension of the measurement vector, 'Y*t', and `T*bar` is the  number of time periods minus 1 (due to the autoregressive structure of the model).

# Fields

  * `Y::AbstractArray{T, N}` : The underlying data array (N-dimensional, element type `<: Real`).
  * `M::Int` : The first dimension of `Y` if `Y` is at least 2D. If `N == 1`, we define `M = 1`.
  * `T_bar::Int` : One less than the “second dimension” in a 2D case, or `length(Y) - 1` for a 1D vector.
