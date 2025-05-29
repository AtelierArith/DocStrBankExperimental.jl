```
mutable struct δWishart{T,D} <: δDistribution
    μ
end
```

[`Wishart`](@ref) 分布の δ-同等物。

# コンストラクタ

```
δWishart{T,D}()
δWishart(μ)
```

ここで `T` はパラメータのエンコーディングタイプで、`μ` はディラック δ パルスの位置です。

# 例

```jldoctest
julia> δWishart{Float32,2}()
δWishart{Float32,2}:
  μ = Float32[1.0 0.0; 0.0 1.0]

julia> using LinearAlgebra; δWishart(Symmetric([1 0.5; 0.5 1]))
δWishart{Float64,2}:
  μ = [1.0 0.5; 0.5 1.0]
```
