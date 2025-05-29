```
weighted_movmean!(z::AbstractVector{FT}, x::AbstractVector{Tx}, w::AbstractVector{Tw}, 
    win::Tuple{Int,Int}=(1, 1); skip_centre=false) where {FT<:Real,Tx<:Real,Tw<:Real}
```

Calculate the weighted moving mean of the input vector `x` using the window defined by `win` and the specified `weights`, and store the result in the preallocated output vector `z`.

# Arguments

  * `z`: Preallocated output vector to store the computed weighted moving mean values.
  * `x`: Input vector of real numbers.
  * `w`: Vector of weights to be applied to the elements within the window. The length of `weights` should be equal to the window size `(win_left + win_right + 1)`.
  * `win`: A tuple `(win_left, win_right)` specifying the window size. Default is `(1, 1)`.
  * `skip_centre`: If `true`, the current element is skipped during the calculation.

# Returns

The output vector `z` containing the weighted moving mean values.

# Example

```julia
x = [1.0, 2.0, 3.0, 4.0, 5.0]
w = [0.1, 0.8, 0.1]
z = similar(x, Float64)
weighted_movmean!(z, x, w, (1, 1); skip_centre=false)
```
