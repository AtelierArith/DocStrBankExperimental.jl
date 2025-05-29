```
ℓ¹(::Weight)
ℓ¹(::Tuple{Vararg{Weight}})
ℓ¹()
ℓ¹(::Weight...)
```

重み付き $\ell^1$ 空間を表す [`Ell1`](@ref) のUnicodeエイリアスです。

# 例

```jldoctest
julia> ℓ¹()
ℓ¹()

julia> ℓ¹(GeometricWeight(1.0))
ℓ¹(GeometricWeight(1.0))

julia> ℓ¹(GeometricWeight(1.0), AlgebraicWeight(2.0))
ℓ¹(GeometricWeight(1.0), AlgebraicWeight(2.0))
```
