```
fits_write_col(f, colnum, firstrow, firstelem, data)
```

ASCII/バイナリテーブルの1つの列にデータを書き込みます。

要素を格納するスペースがない場合は、新しい行が作成されます。（したがって、テーブルの末尾に要素を*追加*するだけの場合は、[`fits_insert_rows`](@ref)を呼び出すことは無意味です。）

  * `f::FITSFile`: データが書き込まれるファイル。
  * `colnum::Integer`: 列番号、最初の列の値は`1`です。
  * `firstrow::Integer`: この行からデータが書き込まれます。
  * `firstelem::Integer`: 最初の要素が書き込まれる行内の位置を指定します。
  * `data::Array`: テーブルの列に書き込まれる要素を含みます。
