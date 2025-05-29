```
qrm_least_squares!(spmat, b, x; transp='n')
```

この関数は線形最小二乗問題を解くために使用できます

$$
\min \|Ax − b\|_2
$$

入力行列が正方形または過剰決定されている場合のショートカットです。これは次のシーケンスのショートカットです

```
qrm_analyse!(spmat, spfct; transp='n')
qrm_factorize!(spmat, spfct; transp='n')
qrm_apply!(spfct, b; transp='t')
qrm_solve!(spfct, b, x; transp='n')
```

#### 入力引数 :

  * `spmat`: 入力行列。
  * `b`: 右辺。
  * `x`: 解ベクトル。
  * `transp`: A, Aᵀ または Aᴴ を使用するかどうか。`'t'`、`'c'` または `'n'` のいずれかです。
