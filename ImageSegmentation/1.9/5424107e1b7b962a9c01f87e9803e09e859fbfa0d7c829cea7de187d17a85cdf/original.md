```
mask = flood(f, src, idx, nbrhood_function=diamond_iterator((3,3,...)))
```

Return an array `mask` with the same axes as `src`, marked `true` for all elements of `src` that:

  * satisfy `f(src[i]) == true` and
  * are connected by such elements to the starting point `idx` (an integer index or `CartesianIndex`).

This throws an error if `f` evaluates as `false` for the starting value `src[idx]`. The sense of connectivity is defined by `nbrhood_function`, with two choices being [`ImageSegmentation.diamond_iterator`](@ref) and [`ImageSegmentation.box_iterator`](@ref.)

# Examples

```jldoctest; setup=:(using ImageSegmentation, ImageCore)
julia> mostly_red(c) = red(c) > green(c) && red(c) > blue(c)
mostly_red (generic function with 1 method)

julia> img = repeat(LinRange(colorant"red", colorant"blue", 4), 1, 2) # red-to-blue
4×2 Matrix{RGB{Float32}}:
 RGB(1.0, 0.0, 0.0)            RGB(1.0, 0.0, 0.0)
 RGB(0.666667, 0.0, 0.333333)  RGB(0.666667, 0.0, 0.333333)
 RGB(0.333333, 0.0, 0.666667)  RGB(0.333333, 0.0, 0.666667)
 RGB(0.0, 0.0, 1.0)            RGB(0.0, 0.0, 1.0)

julia> flood(mostly_red, [img; img], 1)   # only first copy of `img` is connected
8×2 BitMatrix:
 1  1
 1  1
 0  0
 0  0
 0  0
 0  0
 0  0
 0  0
```

See also [`flood_fill!`](@ref).
