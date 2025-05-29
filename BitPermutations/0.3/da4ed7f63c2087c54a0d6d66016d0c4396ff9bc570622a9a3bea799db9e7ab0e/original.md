```
bitpermute(x::Number, p::AbstractBitPermutation)
bitpermute(x::Number, backend::PermutationBackend)
bitpermute(x::AbstractArray{T}, p::AbstractBitPermutation{T})
```

Perform a permutation the bits in `x` using an `AbstractBitPermutation`, using the permutation specified in `p`. The syntax `p(x)` can be used as well. Internally, the permutation operations are stored as a `PermutationBackend`, so the permutation can be called using the backend directly. If the input is an `AbstractArray` subtype, the permutation is performed element-wise. This can be called as well with `p.(x)` or `bitpermute.(x, p)`. For cases in which the input array is not needed afterwards, the in-place version `bitpermute!` is preferred.

See also [`invbitpermute`](@ref), [`bitpermute!`](@ref).
