```
bitpermute!(x::AbstractArray{T}, P::AbstractBitPermutation{T})
```

Perform the  permutation of the bits in each element of `x` using an `AbstractBitPermutation` in place, i.e. by mutating the array `x`.

See also [`bitpermute`](@ref).
