```
cormatgen_constant_noised(n::Int, α::Real; ϵ::Real = (1 .-α)/2.)
```

サイズ n x n の定数相関行列を返し、定数相関は 0 <= α <= 1 で、追加のノイズは ϵ によって決まります。

```julia
julia> Random.seed!(43);

julia> cormatgen_constant_noised(3, 0.5)
3×3 Array{Float64,2}:
 1.0       0.506271  0.285793
 0.506271  1.0       0.475609
 0.285793  0.475609  1.0
```
