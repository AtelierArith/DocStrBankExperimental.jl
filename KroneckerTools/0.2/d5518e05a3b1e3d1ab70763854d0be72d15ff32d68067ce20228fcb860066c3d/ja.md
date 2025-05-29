```
a_mul_kron_b!(c::AbstractVector, a::AbstractVecOrMat, b::AbstractMatrix, order::Int64)
```

a*(b ⊗ b ⊗ ... ⊗ b) を実行します。解は行列 c に返されます。order は b の出現回数を示します。

次のように使用します：vec(a*(b ⊗ b ⊗ ... ⊗ b)) = (b' ⊗ b' ⊗ ... ⊗ b' ⊗ I)vec(a) ```
