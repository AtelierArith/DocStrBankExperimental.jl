```
mutable struct δNormalDiag{T,D} <: δDistribution
    μ
end
```

[`NormalDiag`](@ref) 分布の δ 等価物。

# コンストラクタ

```
δNormalDiag{T,D}()
δNormalDiag(μ)
```

ここで `T` はパラメータのエンコーディングタイプ、`D` はサポートの次元、`μ` はディラック δ パルスの位置です。

# 例

```jldoctest
julia> δNormalDiag{Float32, 2}()
δNormalDiag{Float32,2}:
  μ = Float32[0.0, 0.0]

julia> δNormalDiag([1.0, 1.0])
δNormalDiag{Float64,2}:
  μ = [1.0, 1.0]
```
