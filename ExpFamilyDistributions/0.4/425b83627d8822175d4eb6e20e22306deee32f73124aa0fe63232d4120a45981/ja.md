```
mutable struct NormalDiag{T,D} <: ExpFamilyDistribution
    μ
    v
end
```

対角共分散行列を持つ正規分布。`v` は共分散行列の対角成分です。プロパティ `Σ` を使用することで、完全な共分散行列にアクセスすることもできます。

# コンストラクタ

```
NormalDiag{T,D}()
NormalDiag(μ[, v])
```

ここで、`T` はパラメータのエンコーディングタイプ、`D` はサポートの次元、`μ` はベクトル、`v` は共分散行列の対角成分です。

# 例

```jldoctest
julia> NormalDiag{Float32, 2}()
NormalDiag{Float32,2}
  μ = Float32[0.0, 0.0]
  v = Float32[1.0, 1.0]

julia> NormalDiag([1.0, 1.0])
NormalDiag{Float64,2}
  μ = [1.0, 1.0]
  v = [1.0, 1.0]

julia> NormalDiag([1.0, 1.0], [2.0, 1.0])
NormalDiag{Float64,2}
  μ = [1.0, 1.0]
  v = [2.0, 1.0]
```
