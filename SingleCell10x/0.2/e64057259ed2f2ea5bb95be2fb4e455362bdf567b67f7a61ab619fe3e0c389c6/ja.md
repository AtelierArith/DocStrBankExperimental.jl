```
read10x_matrix(io, [matrixtype=SparseMatrixCSC{Int,Int}; transpose=false)
```

10x (CellRanger) カウントマトリックスを読み込みます。`io` はファイル名 (".h5" または ".mtx[.gz]")、`HDF5.File` ハンドル、または IO オブジェクトです。

返されるカウントマトリックスは `matrixtype` 型で、次のいずれかになります：

  * `SparseMatrixCSC` - Julia の標準的なスパースマトリックス形式で、`SparseArrays` にあります。
  * `Matrix` - 標準的な密行列。

`transpose` が `true` の場合、データマトリックスは転置されて読み込まれます。

関連情報: [`read10x`](@ref), [`read10x_barcodes`](@ref), [`read10x_features`](@ref)
