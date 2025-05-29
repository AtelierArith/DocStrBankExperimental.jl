```
mutable struct Gamma{T} <: ExpFamilyDistribution
    α
    β
end
```

ガンマ分布。

# コンストラクタ

```
Gamma{T}()
Gamma{T}(α, β)
```

ここで `T` はパラメータのエンコーディングタイプです。`α` と `β` は分布のパラメータです。

# 例

```jldoctest
julia> Gamma{Float32}()
Gamma{Float32}:
  α = 1.0
  β = 1.0

julia> Gamma{Float64}(1, 2)
Gamma{Float64}:
  α = 1.0
  β = 2.0
```
