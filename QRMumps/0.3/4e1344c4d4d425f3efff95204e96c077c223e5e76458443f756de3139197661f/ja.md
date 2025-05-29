```
qrm_least_squares_semi_normal!(spmat, b, x, z, Δx, y; transp='n')
```

この関数は、線形最小二乗問題を解くために使用できます

$$
\min \|Ax − b\|_2
$$

Aが正方行列または過剰決定の場合に適用されます。`qrm_least_squares!`とは異なり、この関数はAのQR分解のQ因子を保存せずに問題を解くことを可能にします。

これは次のシーケンスのショートカットです

```
qrm_set(spfct, "qrm_keeph", 0)
qrm_analyse!(spmat, spfct, transp  = 'n')
qrm_factorize!(spmat, spfct, transp = 'n')
qrm_spmat_mv!(spmat, T(1), b, T(0), z, transp = 't')
qrm_solve!(spfct, z, y, transp = 't')
qrm_solve!(spfct, y, x, transp = 'n')
qrm_refine!(spmat, spfct, x, z, Δx, y)
```

このシーケンスではQ因子は使用されず、AとRのみが使用されることに注意してください。

#### 入力引数

  * `spmat`: 入力行列。
  * `spfct`: `qrm_spfct`型のスパース因子化オブジェクト。
  * `b`: 右辺。
  * `x`: 解ベクトル。
  * `Δx`: 解を計算するために使用される補助ベクトル（またはbとxが行列の場合は行列）、このベクトル（または行列）のサイズはxと同じで、関数が呼び出されるときに初期化されていなくてもかまいません。
  * `z`: z = Aᵀbの値を格納するために使用される補助ベクトル（またはbとxが行列の場合は行列）、このベクトル（または行列）のサイズはxと同じで、関数が呼び出されるときに初期化されていなくてもかまいません。
  * `y`: 解を計算するために使用される補助ベクトル（またはbとxが行列の場合は行列）、このベクトル（または行列）のサイズはbと同じで、関数が呼び出されるときに初期化されていなくてもかまいません。
  * `transp`: A、AᵀまたはAᴴを使用するかどうか。`'t'`、`'c'`または`'n'`のいずれかです。
