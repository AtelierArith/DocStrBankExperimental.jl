```
movmean(x::AbstractVector{T}, win::Tuple{Int,Int}=(1, 1); skip_centre=false) where {T<:Real}
```

Compute the moving mean of the input vector `x` with a specified window size.

# Arguments

  * `x::AbstractVector{T}`: Input vector of type `T` where `T` is a subtype of `Real`.
  * `win::Tuple{Int,Int}`: A tuple specifying the window size `(win_left, win_right)`. Default is `(1, 1)`.
  * `skip_centre::Bool`: If `true`, the center element is skipped in the mean calculation. Default is `false`.

# Returns

  * A vector of the same length as `x` containing the moving mean values.

# Example

```julia
x = [1.0, 2.0, 3.0, 4.0, 5.0]
movmean(x, (1, 1))  # returns [1.5, 2.0, 3.0, 4.0, 4.5]
movmean(x, (1, 1); skip_centre=true)  # returns [1.0, 2.0, 3.0, 4.0, 5.0]
```
