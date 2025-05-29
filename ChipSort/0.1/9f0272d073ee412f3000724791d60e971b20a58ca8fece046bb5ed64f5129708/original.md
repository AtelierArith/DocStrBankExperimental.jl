```
chipsort_medium!(data, Val(V), Val(J), Val(K))
```

Sort a medium array in-place. The data is divided between `K` blocks of `J` SIMD vectors of size `V`. The array should typically fit inside lower levels of cache memory (L1 or L2), for instance 8192 Int32 values on an conventional desktop computer. Our recipe is:

  * Generate small sorted vectors.
  * Use vectorized Comb sort.
  * Transpose in-place.
  * Finish with insertion sort over the nearly sorted array.

# Examples

```jldoctest
julia> chipsort_medium!(Int32[1:2^13...] .* 0xf0ca .%0x10000, Val(8), Val(8), Val(64))'
1×8192 LinearAlgebra.Adjoint{Int32,Array{Int32,1}}:
 30  32  34  36  38  70  72  74  76  108  110  112  114  116  …  65488  65490  65492  65494  65496  65528  65530  65532  65534
```
