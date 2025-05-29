```
mmread(filename, infoonly=false, retcoord=false)
```

Matrix Marketファイル`filename`の内容を行列に読み込みます。これは、Matrix Market形式によって示されるように、疎行列または密行列のいずれかになります（`coordinate`（座標疎ストレージ）または`array`（密配列ストレージ））。

# 引数

  * `filename::String`: 読み込むファイル。
  * `infoonly::Bool=false`: ヘッダーを読み込むことでサイズと構造に関する情報のみが返されます。行列要素の実際のデータは解析されません。
  * `retcoord::Bool`: `true`の場合、行、列、値のベクトルがヘッダー情報とともに返されます。
