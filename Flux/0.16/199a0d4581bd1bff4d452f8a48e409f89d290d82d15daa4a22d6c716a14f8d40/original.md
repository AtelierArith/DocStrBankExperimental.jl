```
AdaptiveMaxPool(out::NTuple)
```

Adaptive max pooling layer. Calculates the necessary window size such that its output has `size(y)[1:N] == out`.

Expects as input an array with `ndims(x) == N+2`, i.e. channel and batch dimensions, after the `N` feature dimensions, where `N = length(out)`.

See also [`MaxPool`](@ref), [`AdaptiveMeanPool`](@ref).

# Examples

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);  # batch of 50 RGB images

julia> AdaptiveMaxPool((25, 25))(xs) |> size
(25, 25, 3, 50)

julia> MaxPool((4,4))(xs) ≈ AdaptiveMaxPool((25, 25))(xs)
true
```
