```
cormatgen(n::Int = 20)
```

サイズ n x n の対称相関行列 Σ を返します。方法：

```
a = rand(n,n)
b = a*a'
c = b./maximum(b)
```

例：

```jldoctest
julia> Random.seed!(43);

julia> cormatgen(2)
2×2 Array{Float64,2}:
 1.0       0.660768
 0.660768  1.0
```
