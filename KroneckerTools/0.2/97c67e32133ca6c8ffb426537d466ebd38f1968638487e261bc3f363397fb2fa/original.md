```
function kron_at_kron_b_mul_c!(d::AbstractVector, a::AbstractMatrix, order::Int64, b::AbstractMatrix, c::AbstractVector, work1::AbstractVector, work2::AbstractVector)
```

computes d = (a^T ⊗ a^T ⊗ ... ⊗ a^T ⊗ b)c using work vectors work1 and work2
