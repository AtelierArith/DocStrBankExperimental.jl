```
a_mul_kron_b!(c::AbstractVector, a::AbstractVecOrMat, b::AbstractMatrix, order::Int64)
```

Performs a*(b ⊗ b ⊗ ... ⊗ b). The solution is returned in matrix c. order indicates the number of occurences of b

We use vec(a*(b ⊗ b ⊗ ... ⊗ b)) = (b' ⊗ b' ⊗ ... ⊗ b' ⊗ I)vec(a)
