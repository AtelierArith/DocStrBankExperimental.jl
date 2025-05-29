```
mutable struct δNormal{T,D} <: δDistribution
    μ
end
```

[`Normal`](@ref) 分布の δ 同等物。

# コンストラクタ

```
δNormal{T,D}()
δNormal(μ)
```

ここで `T` はパラメータのエンコーディングタイプ、`D` はサポートの次元、`μ` はディラック δ パルスの位置です。

# 例

```jldoctest
julia> δNormal{Float32,2}()
δNormal{Float32,2}:
  μ = Float32[0.0, 0.0]

julia> δNormal([1.0, 1.0])
δNormal{Float64,2}:
  μ = [1.0, 1.0]
```
