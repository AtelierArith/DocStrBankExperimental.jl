```
ExtendedTropical{K,TO} <: Number
ExtendedTropical{K}(orders)
```

最大の `K` 順序を保持する拡張トロピカル数、または係数のない [`TruncatedPoly`](@ref)、`TO` は順序の要素タイプであり、通常は [`Tropical`](@ref) 数です。この代数は次のようにマッピングされます。

  * `+` は二つの集合の和集合の中で最大の `K` 値を見つけることに対応します。
  * `*` は二つの集合の和の組み合わせの中で最大の `K` 値を見つけることに対応します。
  * `0` はセット [-Inf, -Inf, ..., -Inf, -Inf] に対応します。
  * `1` はセット [-Inf, -Inf, ..., -Inf, 0] に対応します。

## フィールド

  * `orders` は最大-K 解のサイズ（解）としての [`Tropical`](@ref) ([`CountingTropical`](@ref)) 数のベクトルです。

## 例

```jldoctest; setup=(using GenericTensorNetworks)
julia> x = ExtendedTropical{3}(Tropical.([1.0, 2, 3]))
ExtendedTropical{3, Tropical{Float64}}(Tropical{Float64}[1.0ₜ, 2.0ₜ, 3.0ₜ])

julia> y = ExtendedTropical{3}(Tropical.([-Inf, 2, 5]))
ExtendedTropical{3, Tropical{Float64}}(Tropical{Float64}[-Infₜ, 2.0ₜ, 5.0ₜ])

julia> x * y
ExtendedTropical{3, Tropical{Float64}}(Tropical{Float64}[6.0ₜ, 7.0ₜ, 8.0ₜ])

julia> x + y
ExtendedTropical{3, Tropical{Float64}}(Tropical{Float64}[2.0ₜ, 3.0ₜ, 5.0ₜ])

julia> one(x)
ExtendedTropical{3, Tropical{Float64}}(Tropical{Float64}[-Infₜ, -Infₜ, 0.0ₜ])

julia> zero(x)
ExtendedTropical{3, Tropical{Float64}}(Tropical{Float64}[-Infₜ, -Infₜ, -Infₜ])
```
