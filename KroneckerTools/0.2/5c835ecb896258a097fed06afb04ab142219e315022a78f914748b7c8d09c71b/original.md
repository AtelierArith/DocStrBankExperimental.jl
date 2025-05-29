```
a_mul_b_kron_c_d!(d::AbstractVecOrMat, a::AbstractVecOrMat, b::AbstractMatrix, c::AbstractMatrix, order::Int64)
```

Performs e = a*b*(c ⊗ d ⊗ ... ⊗ d). The solution is returned in matrix or vector e order indicates the number of occurences of d plus 1. c and d must be square matrices

We use vec(a*b*(c ⊗ d ⊗ ... ⊗ d)) = (c' ⊗ d' ⊗ ... ⊗ d' ⊗ a)vec(b)
