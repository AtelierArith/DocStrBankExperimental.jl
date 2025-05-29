```
invbitpermute(x::Number, p::AbstractBitPermutation)
invbitpermute(x::Number, backend::PermutationBackend)
invbitpermute(x::AbstractArray{T}, P::AbstractBitPermutation{T})
```

Perform the inverse permutation of the bits in `x` using an `AbstractBitPermutation`, using the inverse of the permutation specified in `p`. The syntax `p'(x)` can be used as well. Internally, the permutation operations are stored as a `PermutationBackend`, so the permutation can be called using the backend directly. If the input is an `AbstractArray` subtype, the inverse permutation is performed element-wise. This can be called as well with `p'.(x)` or `invbitpermute.(x, p)`. For cases in which the input array is not needed afterwards, the in-place version `invbitpermute!` is preferred.

See also [`bitpermute`](@ref), [`invbitpermute!`](@ref).
