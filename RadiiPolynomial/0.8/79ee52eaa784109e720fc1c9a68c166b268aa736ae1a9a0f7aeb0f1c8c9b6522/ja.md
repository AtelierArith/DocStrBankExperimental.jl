```
ℓ²(::Weight)
ℓ²(::Tuple{Vararg{Weight}})
ℓ²()
ℓ²(::Weight...)

[`Ell2`](@ref) のユニコードエイリアスで、重み付き $\ell^2$ 空間を表します。

# 例

```

jldoctest julia> ℓ²() ℓ²()

julia> ℓ²(BesselWeight(1.0)) ℓ²(BesselWeight(1.0))

julia> ℓ²(BesselWeight(1.0), GeometricWeight(2.0)) ℓ²(BesselWeight(1.0), GeometricWeight(2.0)) ```
