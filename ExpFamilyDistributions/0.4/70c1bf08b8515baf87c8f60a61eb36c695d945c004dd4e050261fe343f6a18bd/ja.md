```
mutable struct δGamma{T} <: δDistribution
    μ
end
```

[`Gamma`](@ref)分布のδ同等物。

# コンストラクタ

```
δGamma{T}()
δGamma{T}(μ)
```

ここで、`T`はパラメータのエンコーディングタイプで、`μ`はディラックδパルスの位置です。

# 例

```jldoctest
julia> δGamma{Float32}()
δGamma{Float32}:
  μ = 1.0

julia> δGamma{Float64}(2)
δGamma{Float64}:
  μ = 2.0
```
