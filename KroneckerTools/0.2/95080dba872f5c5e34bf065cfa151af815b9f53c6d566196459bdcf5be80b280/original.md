```
function kron_at_kron_b_mul_c!(a::AbstractMatrix, order::Int64, b::AbstractMatrix, c::AbstractVector, offset_c::Int64, work::AbstractVector)
```

updates c at offset_c with (a^T ⊗ a^T ⊗ ... ⊗ a^T ⊗ b)c using c and work as work vectors
