```
fock(i, hspace_size,T::Type{<:Complex}=ComplexF64)
```

サイズ `hspace_size` のヒルベルト空間の `i` 番目のフォック基底をケットとして返します。

!!! note
    フォック基底状態の番号付けは 0 から始まります。


ケットにはデフォルトで ComplexF64 の型 `T` の値が含まれています。

# 例

```jldoctest
julia> ψ = fock(0, 3)
3-element Ket{ComplexF64}:
1.0 + 0.0im
0.0 + 0.0im
0.0 + 0.0im


julia> ψ = fock(1, 3)
3-element Ket{ComplexF64}:
0.0 + 0.0im
1.0 + 0.0im
0.0 + 0.0im


julia> ψ = fock(1, 3, ComplexF32) # ComplexF64 以外の型を指定
3-element Ket{ComplexF32}:
0.0f0 + 0.0f0im
1.0f0 + 0.0f0im
0.0f0 + 0.0f0im
```
