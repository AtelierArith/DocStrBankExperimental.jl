```
mutable struct Dirichlet{T,D} <: δDistribution
    μ
end
```

[`Dirichlet`](@ref)分布のδ等価。

# コンストラクタ

```
Dirichlet{T,D}()
Dirichlet(μ)
```

ここで、`T`はパラメータのエンコーディングタイプ、`D`はサポートの次元、`μ`はディラックδパルスの位置です。

# 例

```jldoctest
julia> δDirichlet{Float32, 2}()
δDirichlet{Float32,2}:
  μ = Float32[0.5, 0.5]

julia> δDirichlet(Float32[1/2, 1/2])
δDirichlet{Float32,2}:
  μ = Float32[0.5, 0.5]
```
