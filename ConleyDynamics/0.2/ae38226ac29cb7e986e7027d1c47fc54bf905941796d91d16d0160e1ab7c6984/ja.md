```
lefschetz_information(lc::LefschetzComplex)
```

Lefschetz複体に関する基本情報を抽出します。

入力引数`lc`はLefschetz複体を含みます。この関数は情報を`Dict{String,Any}`の形式で返します。返される辞書のキーセットを見るには、コマンド`keys`を使用できます：

  * `"Dimension"`: Lefschetz複体の次元
  * `"Coefficient field"`: 基本の係数体
  * `"Euler characteristic"`: 複体のオイラー特徴量
  * `"Homology"`: Lefschetz複体のベッティ数
  * `"Boundary sparsity"`: 境界行列のスパース率
  * `"Number of cells"`: 複体内のセルの総数
  * `"Cell counts by dim"`: 次元ごとのセルの数

最後の場合、辞書のエントリはペアのベクトル`(次元, セルの数)`です。
