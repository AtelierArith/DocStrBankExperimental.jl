```
kpm_eval(A::AbstractMatrix{T}, kpm_expansion::KPMExpansion{T}) where {T<:AbstractFloat}
```

行列 $F(A)$ を評価して返します。ここで、$A$ は厳密に実数の固有値を持つ演算子であり、関数 $F(\bullet)$ はベクトル `coefs` によって与えられる係数を持つチェビシェフ展開によって表されます。
