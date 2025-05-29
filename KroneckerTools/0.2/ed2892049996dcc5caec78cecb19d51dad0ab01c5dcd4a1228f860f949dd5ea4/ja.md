```
a_mul_b_kron_c!(d::AbstractVecOrMat, a::AbstractVecOrMat, b::AbstractMatrix, c::AbstractMatrix, order::Int64)
```

a*B*(c ⊗ c ⊗ ... ⊗ c) を実行します。解は行列またはベクトル d に返されます。order は c の出現回数を示します。c は正方行列でなければなりません。

vec(a*b*(c ⊗ c ⊗ ... ⊗ c)) = (c' ⊗ c' ⊗ ... ⊗ c' ⊗ a)vec(b) を使用します。
