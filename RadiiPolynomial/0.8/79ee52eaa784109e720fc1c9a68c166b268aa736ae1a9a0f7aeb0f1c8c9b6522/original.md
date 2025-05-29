```
ℓ²(::Weight)
ℓ²(::Tuple{Vararg{Weight}})
ℓ²()
ℓ²(::Weight...)
```

Unicode alias of [`Ell2`](@ref) representing the weighted $\ell^2$ space.

# Examples

```jldoctest
julia> ℓ²()
ℓ²()

julia> ℓ²(BesselWeight(1.0))
ℓ²(BesselWeight(1.0))

julia> ℓ²(BesselWeight(1.0), GeometricWeight(2.0))
ℓ²(BesselWeight(1.0), GeometricWeight(2.0))
```
