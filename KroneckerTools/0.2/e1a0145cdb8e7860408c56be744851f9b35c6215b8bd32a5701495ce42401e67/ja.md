```
function kron_at_kron_b_mul_c!(d::AbstractVector, offset_d::Int64, a::AbstractMatrix, order::Int64, b::AbstractMatrix, c::AbstractVector, offset_c::Int64, work1::AbstractVector, work2::AbstractVector, offset_w::Int64)
```

は、d = (a^T ⊗ a^T ⊗ ... ⊗ a^T ⊗ b)c を計算します。これは、c の offset*c からのデータと、offset*w の work ベクトル work1 と work2 を使用します。
