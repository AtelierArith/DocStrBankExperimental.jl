```
movstd!(z::AbstractVector{FT}, x::AbstractVector{T}, win::Tuple{Int,Int}=(1, 1);
      skip_centre=false, ddof=1) where {FT<:Real, T<:Real}
```

Calculate the moving standard deviation of the input vector `x` using the window defined by `win` and store the result in the preallocated output vector `z`.

# Arguments

  * `z`: Preallocated output vector to store the computed standard deviation values.
  * `x`: Input vector of real numbers.
  * `win`: A tuple `(win_left, win_right)` specifying the window size. Default is `(1, 1)`.
  * `skip_centre`: If `true`, the current element is skipped during the calculation.
  * `ddof`: Delta degrees of freedom for variance calculation. The variance is computed as `(∑x² - ∑x*μ) / (N - ddof)`.

# Returns

The output vector `z` containing the moving standard deviation. If the number of valid values in the window is not greater than `ddof`, `NaN` is assigned to that position.

# Example

```julia
x = [1.0, 2.0, 3.0, 4.0, 5.0]
z = similar(x, Float64)
movstd!(z, x, (1, 1); skip_centre=false, ddof=1)
```
