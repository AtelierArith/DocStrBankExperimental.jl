```
convolve(A, B=3)
```

yields the discrete convolution of array `A` by the kernel defined by `B`. The result `dst` is an array similar to `A`.

Using `Idx(A)` to denote the set of valid indices for array `A` and assuming `B` is an array of values, the discrete convolution of `A` by `B` writes:

```
dst = similar(A, T)
for i ∈ Idx(dst)
    v = zero(T)
    @inbounds for j ∈ Idx(A) ∩ (i - Idx(B))
        v += A[j]*B[i-j]
    end
    dst[i] = v
end
```

with `T` the type of the sum of the products of the elements of `A` and `B`, and where `Idx(A) ∩ (i - Idx(B))` denotes the subset of indices `j` such that `j ∈ Idx(A)` and `i - j ∈ Idx(B)` and thus for which `A[j]` and `B[i-j]` are valid.

See also [`convolve!`](@ref) and [`localfilter!`](@ref).
