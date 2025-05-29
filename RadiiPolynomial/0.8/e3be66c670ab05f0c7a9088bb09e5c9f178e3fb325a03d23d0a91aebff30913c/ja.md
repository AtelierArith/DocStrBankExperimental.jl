```
ℓ∞(::Weight)
ℓ∞(::Tuple{Vararg{Weight}})
ℓ∞()
ℓ∞(::Weight...)
```

重み付き $\ell^\infty$ 空間を表す [`EllInf`](@ref) のUnicodeエイリアスです。

# 例

```jldoctest
julia> ℓ∞()
ℓ∞()

julia> ℓ∞(GeometricWeight(1.0))
ℓ∞(GeometricWeight(1.0))

julia> ℓ∞(GeometricWeight(1.0), AlgebraicWeight(2.0))
ℓ∞(GeometricWeight(1.0), AlgebraicWeight(2.0))
```
