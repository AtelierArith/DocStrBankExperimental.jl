```
read10x(io, [matrixtype=SparseMatrixCSC{Int,Int}, featuretype=NamedTuple, barcodetype=Vector];
        transpose=false, [features, barcodes, delim])
```

10x (CellRanger) カウントマトリックスとアノテーションを読み込みます。`io` はファイル名 (".h5" または "[prefix]matrix.mtx[.gz]") または `HDF5.File` ハンドルです。注意: 入力ファイル名が "[prefix]matrix.mtx[.gz]" の場合、同じフォルダ内で一致するフィーチャーおよびバーコードファイルが検索されます。

返されるカウントマトリックスは `matrixtype` 型であり、次のいずれかになります:

  * `SparseMatrixCSC` - Julia の標準スパースマトリックス形式で、`SparseArrays` にあります。
  * `Matrix` - 標準の密行列。

返されるバーコード/フィーチャーのアノテーションは `barcodetype`/`featuretype` 型であり、次のいずれかになります:

  * NamedTuple - 列名をキー、列ベクトルを値とする。
  * Vector - バーコードのみ。
  * DataFrame - `DataFrames` パッケージを参照。
  * NamedTuples から構築できる他のテーブル型。
  * NamedTuple (features) または Vector (barcodes) を入力として受け取るユーザー定義の関数/型コンストラクタ。

`transpose` が `true` の場合、データマトリックスは転置された状態で読み込まれます。

`features` と `barcodes` は `mtx[.gz]` ファイルのみに許可されます。これらは `features`/`barcodes` のファイルパスを指定するために使用できます。デフォルトでは、ファイルパスは自動検出されます。無効にするには `nothing` に設定します。また、マトリックスファイルパスを入力として受け取り、対応するバーコード/フィーチャーファイルパスを返す関数に設定することもできます。

列区切り文字 `delim` はフィーチャー/バーコードの (tsv|csv) ファイルにのみ使用され、指定されていない場合はファイル名から検出されます。

参照: [`read10x_matrix`](@ref), [`read10x_barcodes`](@ref), [`read10x_features`](@ref)
