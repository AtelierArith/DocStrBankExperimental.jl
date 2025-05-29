```
movmean(x::AbstractVector{T}, win::Tuple{Int, Int}=(1, 1); skip_centre=false) where {T<:Real}
```

Compute the simple moving average of a 1-dimensional array `x` over a window defined by `win`, returning an array of the same size as `x`.

# Arguments

  * `x::AbstractVector{T}`: Input array of type `T`.
  * `win::Tuple{Int64, Int64}`: Tuple defining the window size to the left and right of each element. Default is `(1, 1)`.
  * `skip_centre::Bool`: If `true`, the center element is skipped in the average calculation. Default is `false`.

# Returns

  * `Vector`: An array of the same size as `x` containing the moving averages.

# Example

```julia
x = [1, 2, 3, 4, 5]
win = (1, 1)
movmean(x, win)  # returns [1.5, 2.0, 3.0, 4.0, 4.5]
```
