```
MaxPool(window::NTuple; pad=0, stride=window)
```

Max pooling layer, which replaces all pixels in a block of size `window` with one.

Expects as input an array with `ndims(x) == N+2`, i.e. channel and batch dimensions, after the `N` feature dimensions, where `N = length(window)`.

By default the window size is also the stride in each dimension. The keyword `pad` accepts the same options as for the `Conv` layer, including `SamePad()`.

See also [`Conv`](@ref), [`MeanPool`](@ref), [`AdaptiveMaxPool`](@ref), [`GlobalMaxPool`](@ref).

# Examples

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);  # batch of 50 RGB images

julia> m = Chain(Conv((5, 5), 3 => 7, pad=SamePad()), MaxPool((5, 5), pad=SamePad()))
Chain(
  Conv((5, 5), 3 => 7, pad=2),          # 532 parameters
  MaxPool((5, 5), pad=2),
)

julia> m[1](xs) |> size
(100, 100, 7, 50)

julia> m(xs) |> size
(20, 20, 7, 50)

julia> layer = MaxPool((5,), pad=2, stride=(3,))  # one-dimensional window
MaxPool((5,), pad=2, stride=3)

julia> layer(rand(Float32, 100, 7, 50)) |> size
(34, 7, 50)
```
