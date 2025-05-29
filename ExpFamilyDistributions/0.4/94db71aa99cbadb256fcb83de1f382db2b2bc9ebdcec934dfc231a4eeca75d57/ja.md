```
mutable struct Normal{T,D} <: ExpFamilyDistribution
    μ
    Σ
end
```

完全共分散行列を持つ正規分布。

# コンストラクタ

```
Normal{T,D}()
Normal(μ[, Σ])
```

ここで `T` はパラメータのエンコーディングタイプ、`D` はサポートの次元、`μ` はベクトル、`Σ` は [**対称**](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.Symmetric) 行列です。

# 例

```jldoctest
julia> Normal{Float32,2}()
Normal{Float32,2}:
  μ = Float32[0.0, 0.0]
  Σ = Float32[1.0 0.0; 0.0 1.0]

julia> Normal([1.0, 1.0])
Normal{Float64,2}:
  μ = [1.0, 1.0]
  Σ = [1.0 0.0; 0.0 1.0]

julia> using LinearAlgebra; Normal([1.0, 1.0], Symmetric([2.0 0.5; 0.5 1.0]))
Normal{Float64,2}:
  μ = [1.0, 1.0]
  Σ = [2.0 0.5; 0.5 1.0]
```
