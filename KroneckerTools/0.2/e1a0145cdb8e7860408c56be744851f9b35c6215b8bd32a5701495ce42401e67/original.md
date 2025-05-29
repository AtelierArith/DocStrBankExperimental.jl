```
function kron_at_kron_b_mul_c!(d::AbstractVector, offset_d::Int64, a::AbstractMatrix, order::Int64, b::AbstractMatrix, c::AbstractVector, offset_c::Int64, work1::AbstractVector, work2::AbstractVector, offset_w::Int64)
```

computes d = (a^T ⊗ a^T ⊗ ... ⊗ a^T ⊗ b)c using data from c at offset*c and work vectors work1 and work2 at offset*w
