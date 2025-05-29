```
ℓ∞(::Weight)
ℓ∞(::Tuple{Vararg{Weight}})
ℓ∞()
ℓ∞(::Weight...)
```

Unicode alias of [`EllInf`](@ref) representing the weighted $\ell^\infty$ space.

# Examples

```jldoctest
julia> ℓ∞()
ℓ∞()

julia> ℓ∞(GeometricWeight(1.0))
ℓ∞(GeometricWeight(1.0))

julia> ℓ∞(GeometricWeight(1.0), AlgebraicWeight(2.0))
ℓ∞(GeometricWeight(1.0), AlgebraicWeight(2.0))
```
