```
kpm_eval!(
    F::AbstractMatrix, A, coefs::AbstractVector, bounds,
    tmp = zeros(eltype(F), size(F)..., 4)
)
```

行列 $F(A)$ を `F` に評価して書き込みます。ここで、$A$ は `bounds` 引数で指定された区間 `(bounds[1], bounds[2])` に厳密に実数の固有値を持つ演算子であり、関数 $F(\bullet)$ はベクトル `coefs` で与えられた係数を持つチェビシェフ展開によって表されます。最後に、`tmp` は動的メモリ割り当てを避けるために使用されます。
