```
ℓ¹(::Weight)
ℓ¹(::Tuple{Vararg{Weight}})
ℓ¹()
ℓ¹(::Weight...)
```

Unicode alias of [`Ell1`](@ref) representing the weighted $\ell^1$ space.

# Examples

```jldoctest
julia> ℓ¹()
ℓ¹()

julia> ℓ¹(GeometricWeight(1.0))
ℓ¹(GeometricWeight(1.0))

julia> ℓ¹(GeometricWeight(1.0), AlgebraicWeight(2.0))
ℓ¹(GeometricWeight(1.0), AlgebraicWeight(2.0))
```
