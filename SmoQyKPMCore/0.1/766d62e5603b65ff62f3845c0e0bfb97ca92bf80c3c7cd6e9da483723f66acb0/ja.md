```
kpm_eval!(
    F::AbstractMatrix, A, kpm_expansion::KPMExpansion,
    tmp = zeros(eltype(F), size(F)..., 3)
)
```

行列 $F(A)$ を `F` に評価して書き込みます。ここで、$A$ は厳密に実数の固有値を持つ演算子であり、関数 $F(\bullet)$ はベクトル `coefs` によって与えられる係数を持つチェビシェフ展開で表されます。最後に、配列 `tmp` は動的メモリ割り当てを避けるために使用されます。
