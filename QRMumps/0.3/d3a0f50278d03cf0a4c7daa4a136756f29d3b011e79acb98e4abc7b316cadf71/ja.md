```
qrm_min_norm!(spmat, b, x; transp='n')
```

この関数は線形最小ノルム問題を解くために使用できます

$$
\min \|x\|_2 \quad s.t. \quad Ax = b
$$

入力行列が正方形または過小決定の場合のショートカットです。次のシーケンスのショートカットです。

```
qrm_analyse!(spmat, spfct; transp='t')
qrm_factorize!(spmat, spfct; transp='t')
qrm_solve!(spfct, b, x; transp='t')
qrm_apply!(spfct, x; transp='n')
```

#### 入力引数 :

  * `spmat`: 入力行列。
  * `b`: 右辺。
  * `x`: 解ベクトル。
  * `transp`: A, Aᵀ または Aᴴ を使用するかどうか。`'t'`、`'c'` または `'n'` のいずれかです。
