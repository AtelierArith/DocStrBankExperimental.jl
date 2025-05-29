```
a_mul_b_kron_c_d!(d::AbstractVecOrMat, a::AbstractVecOrMat, b::AbstractMatrix, c::AbstractMatrix, order::Int64)
```

e = a*b*(c ⊗ d ⊗ ... ⊗ d) を実行します。解は行列またはベクトル e として返され、order は d の出現回数に 1 を加えたものを示します。c と d は正方行列でなければなりません。

私たちは次のように使用します：vec(a*b*(c ⊗ d ⊗ ... ⊗ d)) = (c' ⊗ d' ⊗ ... ⊗ d' ⊗ a)vec(b) ```
