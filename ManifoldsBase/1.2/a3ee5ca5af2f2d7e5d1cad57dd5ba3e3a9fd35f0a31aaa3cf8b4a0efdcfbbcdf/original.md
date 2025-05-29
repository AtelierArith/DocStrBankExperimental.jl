```
CachedBasis{𝔽,V,<:AbstractBasis{𝔽}} <: AbstractBasis{𝔽}
```

A cached version of the given `basis` with precomputed basis vectors. The basis vectors are stored in `data`, either explicitly (like in cached variants of [`ProjectedOrthonormalBasis`](@ref)) or implicitly.

# Constructor

```
CachedBasis(basis::AbstractBasis, data)
```
