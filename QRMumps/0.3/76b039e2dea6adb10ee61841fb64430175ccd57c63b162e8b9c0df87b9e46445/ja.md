```
qrm_update!(spmat, A)
qrm_update!(spmat, vals)
```

このルーチンは、**sparseMatrixCSC** から **qrm_spmat** 型データ構造を更新します。`spmat` と `A` は同じスパースパターンを持っている必要があります。

#### 入力引数 :

最初の形式では、

  * `spmat`: 更新される **qrm_spmat** スパース行列。
  * `A` : **SparseMatrixCSC** 形式で保存された Julia スパース行列。

2 番目の形式では、

  * `vals`: `A` の非ゼロ要素の値の配列。
