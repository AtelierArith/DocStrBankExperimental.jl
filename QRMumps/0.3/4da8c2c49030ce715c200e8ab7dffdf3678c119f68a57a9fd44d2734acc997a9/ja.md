```
qrm_spposv!(spmat, b, x)
```

この関数は線形対称正定値問題を解くために使用できます。これは次の手順のショートカットです。

```
x = b
qrm_analyse!(spmat, spfct; transp='n')
qrm_factorize!(spmat, spfct; transp='n')
qrm_solve!(spfct, x, x; transp='t')
qrm_solve!(spfct, x, x; transp='t')
```

#### 入力引数 :

  * `spmat`: 入力行列。
  * `b`: 右辺。
  * `x`: 解ベクトル。
