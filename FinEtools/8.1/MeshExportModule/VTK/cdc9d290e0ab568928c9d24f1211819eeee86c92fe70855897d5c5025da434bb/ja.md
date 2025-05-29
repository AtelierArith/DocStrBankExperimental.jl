```
vtkexportmesh(theFile::String, Connectivity, Points, Cell_type;
    vectors=nothing, scalars=nothing)
```

メッシュをVTK 1.0ファイルとして非構造化グリッドにエクスポートします。

引数:

  * `theFile` = ファイル名,
  * `Connectivity` = 接続の配列、要素ごとに1行,
  * `Points` = ノード座標の配列、ノードごとに1行,
  * `Cell_type` = セルのタイプ、事前定義された定数P1, L2, ..., H20, ...を参照,
  * `scalars` = タプルの配列、(名前, データ)
  * `vectors` = タプルの配列、(名前, データ)

`scalars`について: `data`がベクトルの場合、そのデータは単一のフィールドとしてエクスポートされます。一方、2次元配列の場合は、各列が別々のフィールドとしてエクスポートされます。
