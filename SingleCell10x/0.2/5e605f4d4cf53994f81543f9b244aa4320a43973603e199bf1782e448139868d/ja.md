```
read10x_matrix_metadata(io; transpose=false)
```

10x (CellRanger) カウントマトリックスのメタデータを読み込みます。`io` はファイル名 (".h5" または ".mtx[.gz]")、または `HDF5.File` ハンドル、または IO オブジェクトです。

カウントマトリックスの高さ、幅、非ゼロエントリの数を表す `(P,N,nnz)` を返します。

`transpose` が `true` の場合、`P` と `N` は入れ替わります。

関連情報: [`read10x`](@ref), [`read10x_matrix`](@ref)
