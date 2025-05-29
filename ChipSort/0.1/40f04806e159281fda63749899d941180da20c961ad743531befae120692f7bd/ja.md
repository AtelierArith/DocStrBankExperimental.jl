```
chipsort_small!(data, Val(V), Val(J))
```

ベクトル化されたソートネットワークとビトニックマージネットワークを使用して小さな配列をソートします。最初のソートは、サイズ `V` の `J` SIMD ベクトルに対して行われます。配列は通常、レジスタメモリ内に収まる必要があります。たとえば、AVX2 マシンでは 64 の Int32 値が収まります。

# 例

```jldoctest
julia> chipsort_small!(Int32[1:16...] .* Int32(1729) .%0x100, Val(4), Val(4))'
1×16 LinearAlgebra.Adjoint{Int32,Array{Int32,1}}:
 4  8  12  16  67  71  75  79  130  134  138  142  193  197  201  205
```
