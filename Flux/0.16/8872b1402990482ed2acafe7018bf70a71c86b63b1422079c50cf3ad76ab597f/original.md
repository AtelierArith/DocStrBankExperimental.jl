```
Upsample(mode = :nearest; [scale, size]) 
Upsample(scale, mode = :nearest)
```

An upsampling layer. One of two keywords must be given:

If `scale` is a number, this applies to all but the last two dimensions (channel and batch) of the input.  It may also be a tuple, to control dimensions individually. Alternatively, keyword  `size` accepts a tuple, to directly specify the leading dimensions of the output.

Currently supported upsampling `mode`s  and corresponding NNlib's methods are:

  * `:nearest` -> [`NNlib.upsample_nearest`](@ref)
  * `:bilinear` -> [`NNlib.upsample_bilinear`](@ref)
  * `:trilinear` -> [`NNlib.upsample_trilinear`](@ref)

# Examples

```jldoctest
julia> m = Upsample(scale = (2, 3))
Upsample(:nearest, scale = (2, 3))

julia> m(ones(2, 2, 1, 1)) |> size
(4, 6, 1, 1)

julia> m = Upsample(:bilinear, size = (4, 5))
Upsample(:bilinear, size = (4, 5))

julia> m(ones(2, 2, 1, 1)) |> size
(4, 5, 1, 1)
```
