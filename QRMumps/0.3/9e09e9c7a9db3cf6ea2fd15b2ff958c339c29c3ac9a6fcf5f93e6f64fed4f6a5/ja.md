```
qrm_analyse!(spmat, spfct; transp='n')
```

このルーチンは分析フェーズを実行し、spfctを更新します。

#### 入力引数 :

  * `spmat`: 型 `qrm_spmat` の入力行列。
  * `spfct`: 型 `qrm_spfct` のスパース因子化オブジェクト。
  * `transp`: 入力行列を転置するかどうか。`'t'`、`'c'`、または`'n'`のいずれか。
