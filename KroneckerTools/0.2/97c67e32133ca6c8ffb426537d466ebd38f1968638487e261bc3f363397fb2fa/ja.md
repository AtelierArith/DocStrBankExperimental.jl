```
function kron_at_kron_b_mul_c!(d::AbstractVector, a::AbstractMatrix, order::Int64, b::AbstractMatrix, c::AbstractVector, work1::AbstractVector, work2::AbstractVector)
```

d = (a^T ⊗ a^T ⊗ ... ⊗ a^T ⊗ b)c を作業ベクトル work1 と work2 を使用して計算します。
