```
kpm_eval(A::AbstractMatrix, coefs, bounds)
```

行列 $F(A)$ を評価して返します。ここで、$A$ は `bounds` 引数で指定された区間 `(bounds[1], bounds[2])` に厳密に実数の固有値を持つ演算子であり、関数 $F(\bullet)$ はベクトル `coefs` で与えられた係数を持つチェビシェフ展開によって表されます。
