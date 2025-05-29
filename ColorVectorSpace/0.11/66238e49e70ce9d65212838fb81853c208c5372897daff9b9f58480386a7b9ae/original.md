```
varmult(op, itr; corrected::Bool=true, mean=Statistics.mean(itr), dims=:)
```

Compute the variance of elements of `itr`, using `op` as the multiplication operator. The keyword arguments behave identically to those of `Statistics.var`.

# Example

```julia
julia> cs = [RGB(0.2, 0.3, 0.4), RGB(0.5, 0.3, 0.2)]
2-element Array{RGB{Float64},1} with eltype RGB{Float64}:
 RGB{Float64}(0.2,0.3,0.4)
 RGB{Float64}(0.5,0.3,0.2)

julia> varmult(⋅, cs)
0.021666666666666667

julia> varmult(⊙, cs)
RGB{Float64}(0.045,0.0,0.020000000000000004)

julia> varmult(⊗, cs)
RGBRGB{Float64}:
  0.045  0.0  -0.03
  0.0    0.0   0.0
 -0.03   0.0   0.02
```
