```
qrm_spmat_init!(spmat, A; sym=false)
spmat = qrm_spmat_init!(spmat, m, n, rows, cols, vals; sym=false)
```

このルーチンは、**sparseMatrixCSC** から **qrm_spmat** 型データ構造を初期化します。

#### 入力引数 :

最初の形式では、

  * `spmat`: 初期化される **qrm_spmat** スパース行列。
  * `A` : **SparseMatrixCSC** または **SparseMatrixCOO** 形式で保存された Julia スパース行列（2 番目のケースについては SparseMatricesCOO.jl を参照）。
  * `sym` : 行列が対称 / エルミート (true) か非対称 (false) かを指定するブール値。

2 番目の形式では、行列 `A` は次のように指定されます。

  * `m`: 行数。
  * `n`: 列数。
  * `rows`: 非ゼロ要素の行インデックスの配列。
  * `cols`: 非ゼロ要素の列インデックスの配列。
  * `vals`: 非ゼロ要素の値の配列。
