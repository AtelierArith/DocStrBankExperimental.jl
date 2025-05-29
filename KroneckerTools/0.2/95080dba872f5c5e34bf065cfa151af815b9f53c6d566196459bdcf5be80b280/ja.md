```
function kron_at_kron_b_mul_c!(a::AbstractMatrix, order::Int64, b::AbstractMatrix, c::AbstractVector, offset_c::Int64, work::AbstractVector)
```

は、cとworkを作業ベクトルとして使用して、(a^T ⊗ a^T ⊗ ... ⊗ a^T ⊗ b)cをoffset_cでcを更新します。
