```
MeanPool(window::NTuple; pad=0, stride=window)
```

Mean pooling layer, averaging all pixels in a block of size `window`.

Expects as input an array with `ndims(x) == N+2`, i.e. channel and batch dimensions, after the `N` feature dimensions, where `N = length(window)`.

By default the window size is also the stride in each dimension. The keyword `pad` accepts the same options as for the `Conv` layer, including `SamePad()`.

See also [`Conv`](@ref), [`MaxPool`](@ref), [`AdaptiveMeanPool`](@ref).

# Examples

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);

julia> m = Chain(Conv((5,5), 3 => 7), MeanPool((5,5), pad=SamePad()))
Chain(
  Conv((5, 5), 3 => 7),                 # 532 parameters
  MeanPool((5, 5), pad=2),
)

julia> m[1](xs) |> size
(96, 96, 7, 50)

julia> m(xs) |> size
(20, 20, 7, 50)
```
