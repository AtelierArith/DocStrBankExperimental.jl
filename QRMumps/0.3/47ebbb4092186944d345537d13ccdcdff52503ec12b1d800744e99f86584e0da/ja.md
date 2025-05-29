```
qrm_min_norm_semi_normal!(spmat, spfct, b, x, Δx, y; transp='n')
```

この関数は、線形最小ノルム問題を解くために使用できます

$$
\min \|x\|_2 \quad s.t. \quad Ax = b
$$

Aが正方行列または過小定義の場合に適用されます。`qrm_min_norm!`とは異なり、この関数はAᵀのQR分解においてQ因子を保存せずに問題を解くことを可能にします。これは次のシーケンスのショートカットです

```
qrm_set(spfct, "qrm_keeph", 0)
qrm_analyse!(spmat, spfct, transp = 't')
qrm_factorize!(spmat, spfct, transp = 't')
qrm_solve!(spfct, b, Δx, transp = 't')
qrm_solve!(spfct, Δx, y, transp = 'n')
qrm_spmat_mv!(spmat, T(1),  y, T(0), x, transp = 't')
```

このシーケンスではQ因子は使用されず、むしろAとRが使用されることに注意してください。

#### 入力引数：

  * `spmat`: 入力行列。
  * `spfct`: `qrm_spfct`型のスパース因子化オブジェクト。
  * `b`: 右辺。
  * `x`: 解ベクトル。
  * `Δx`: 解を計算するために使用される補助ベクトル（またはxとbが行列の場合は行列）、このベクトル（または行列）のサイズはxと同じで、関数が呼び出されるときに初期化されていなくてもかまいません。
  * `y`: 解を計算するために使用される補助ベクトル（またはxとbが行列の場合は行列）、このベクトル（または行列）のサイズはbと同じで、関数が呼び出されるときに初期化されていなくてもかまいません。
  * `transp`: A、AᵀまたはAᴴを使用するかどうか。`'t'`、`'c'`または`'n'`のいずれかです。
