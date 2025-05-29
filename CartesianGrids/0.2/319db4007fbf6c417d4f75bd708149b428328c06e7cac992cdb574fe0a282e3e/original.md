```
DDF([ddftype=Roma],[dx=1.0])
```

Construct a discrete delta function operator. This is generally only needed internally by the `Regularize` operator, so the user doesn't have much need for accessing this directly. The default DDF is the `Roma` function, which has a support of 3 grid cells. Other choices are the `Goza` operator, which is a truncated Gaussian with 28 cells support, and the `Witchhat`, which has 2 cells support. The resulting operator is evaluated with one, two or three coordinate arguments, producing, respectively, 1-d, 2-d, or 3-d smeared delta functions. It can also be called with the usual Julia vectorized dot notation with arrays of arguments. The optional cell spacing argument `dx` rescales the coordinates by this spacing, and the result is also rescaled by this spacing (raised to the number of dimensions). This spacing argument defaults to 1.0.

```jldoctest
julia> ddf = DDF(ddftype=Roma)
Discrete delta function operator of type CartesianGrids.Roma, with spacing 1.0

julia> ddf(1)
0.16666666666666666

julia> ddf(-1)
0.16666666666666666

julia> ddf.([-1,0,1])
3-element Array{Float64,1}:
 0.16666666666666666
 0.6666666666666666
 0.16666666666666666
```
