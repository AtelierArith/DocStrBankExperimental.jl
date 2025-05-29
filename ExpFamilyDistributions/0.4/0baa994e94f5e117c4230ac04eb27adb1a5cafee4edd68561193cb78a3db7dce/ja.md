```
mutable struct Wishart{T, D} <: ExpFamilyDistribution
    W
    v
end
```

ウィシャート分布。

# コンストラクタ

```
Wishart{T,D}()
Wishart(W[, v])
```

ここで `T` はパラメータのエンコーディングタイプであり、`W` は [**対称**](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.Symmetric) DxD 行列です。

# 例

```jldoctest
julia> Wishart{Float32,2}()
Wishart{Float32,2}:
  W = Float32[1.0 0.0; 0.0 1.0]
  v = 2.0

julia> using LinearAlgebra; Wishart(Symmetric([1 0.5; 0.5 1]))
Wishart{Float64,2}:
  W = [1.0 0.5; 0.5 1.0]
  v = 2.0
```
