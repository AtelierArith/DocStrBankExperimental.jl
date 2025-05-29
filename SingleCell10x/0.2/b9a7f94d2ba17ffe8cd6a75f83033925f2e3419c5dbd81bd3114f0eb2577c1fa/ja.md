```
read10x_features(io, [featuretype=NamedTuple]; [guess, delim])
```

10xフィーチャーを読み込みます。`io`はファイル名（".h5", ".tsv[.gz]", ".csv[.gz]"または".mtx[.gz]"）または`HDF5.File`ハンドル、またはIOオブジェクトであることができます。

返されるフィーチャーの注釈テーブルは`featuretype`の型であり、次のいずれかになります：

  * NamedTuple - 列名をキー、列ベクトルを値とする。
  * DataFrame - `DataFrames`パッケージを参照してください。
  * NamedTuplesから構築できる他のテーブルタイプ。
  * NamedTupleを入力として受け取るユーザー定義の関数/型コンストラクタ。

入力ファイル名が"[prefix]matrix.mtx[.gz]"の場合、同じフォルダー内で一致するフィーチャーファイルが検索されます。無効にするには`guess=nothing`を設定します。`guess`は、行列ファイルパスを入力として受け取り、対応するフィーチャーファイルパスを返す関数に設定することもできます。

列区切り文字`delim`は、指定されていない場合、ファイル名から検出されます。

参照：[`read10x`](@ref), [`read10x_matrix`](@ref), [`read10x_barcodes`](@ref)
