```
read10x_barcodes(io, [barcodetype=Vector]; [guess, delim])
```

10xバーコードを読み取ります。`io`はファイル名（".h5", ".tsv[.gz]", ".csv[.gz]" または "[prefix]matrix.mtx[.gz]"）または`HDF5.File`ハンドルまたはIOオブジェクトであることができます。

バーコードのために返されるアノテーションオブジェクトは`barcodetype`の型であり、次のいずれかになります：

  * Vector - 各セルのバーコード値を持つ。
  * NamedTuple - "barcode"をキーとし、バーコードベクターを値とする。
  * DataFrame - `DataFrames`パッケージを参照してください。
  * NamedTuplesから構築できる他のテーブルタイプ。
  * NamedTupleを入力として受け取るユーザー定義の関数/型コンストラクタ。

入力ファイル名が"[prefix]matrix.mtx[.gz]"の場合、同じフォルダー内で一致するバーコードファイルが検索されます。`guess=nothing`を設定すると無効になります。`guess`は、行列ファイルパスを入力として受け取り、対応するバーコードファイルパスを返す関数に設定することもできます。

列区切り文字`delim`は、指定されていない場合、ファイル名から検出されます。

参照：[`read10x`](@ref), [`read10x_matrix`](@ref), [`read10x_features`](@ref)
