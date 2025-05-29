```
chipsort_small!(data, Val(V), Val(J))
```

Sort a small array using a vectorized sorting network and bitonic merge networks. The initial sort is over `J` SIMD vectors of size `V`. The array should typically fit inside register memory, for instance 64 Int32 values on an AVX2 machine.

# Examples

```jldoctest
julia> chipsort_small!(Int32[1:16...] .* Int32(1729) .%0x100, Val(4), Val(4))'
1×16 LinearAlgebra.Adjoint{Int32,Array{Int32,1}}:
 4  8  12  16  67  71  75  79  130  134  138  142  193  197  201  205
```
