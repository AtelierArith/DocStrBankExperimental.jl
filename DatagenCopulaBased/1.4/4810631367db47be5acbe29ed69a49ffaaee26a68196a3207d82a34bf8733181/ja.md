```
cormatgen_rand(n::Int = 20)
```

サイズ n x n の対称相関行列 Σ を返します。方法：

```
a = rand(n,n)
b = a*a'
diagb = Matrix(Diagonal(1 ./sqrt.(LinearAlgebra.diag(b))))
b = diagb*b*diagb
```

一般的に cormatgen() よりも高い相関を与えます。例：

```jldoctest
julia> Random.seed!(43);

julia> cormatgen_rand(2)
2×2 Array{Float64,2}:
 1.0       0.879086
 0.879086  1.0
```
