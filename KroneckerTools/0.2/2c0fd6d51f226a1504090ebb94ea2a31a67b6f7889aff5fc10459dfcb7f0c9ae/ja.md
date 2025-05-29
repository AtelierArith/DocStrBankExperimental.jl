```
function kron_at_kron_b_mul_c!(a::AbstractMatrix, order::Int64, b::AbstractMatrix, c::AbstractVector, work::AbstractVector)
```

は、cを更新します (a^T ⊗ a^T ⊗ ... ⊗ a^T ⊗ b)c を使用して、cとworkを作業ベクトルとして使用します。
