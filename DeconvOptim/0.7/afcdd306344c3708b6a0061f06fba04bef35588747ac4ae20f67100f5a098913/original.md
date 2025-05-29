```
Non_negative()
```

Returns a function and an inverse function inverse function to map numbers to non-negative numbers. We use a parabola.

# Examples

```julia-repl
julia> p, p_inv = Non_negative()
(DeconvOptim.var"#5#7"(), DeconvOptim.var"#6#8"())

julia> x = [-1, 2, -3]
3-element Array{Int64,1}:
 -1
  2
 -3

julia> p(x)
3-element Array{Int64,1}:
 1
 4
 9

julia> p_inv(p(x))
3-element Array{Float64,1}:
 1.0
 2.0
 3.0
```
