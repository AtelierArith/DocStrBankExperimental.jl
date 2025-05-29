```
mutable struct Dirichlet{T,D} <: ExpFamilyDistribution
    α
end
```

ディリクレ分布。

# コンストラクタ

```
Dirichlet{T,D}()
Dirichlet(α)
```

ここで `T` はパラメータのエンコーディングタイプ、`D` はサポートの次元、`α` はパラメータのベクトルです。

# 例

```jldoctest
julia> Dirichlet{Float32, 2}()
Dirichlet{Float32,2}:
  α = Float32[1.0, 1.0]

julia> Dirichlet([1.0, 2.0, 3.0])
Dirichlet{Float64,3}:
  α = [1.0, 2.0, 3.0]
```
