```julia
simplexgrid(
    file::String;
    format,
    kwargs...
) -> ExtendableGrids.ExtendableGrid{Float64, Int32}

```

ファイルからグリッドを読み込みます。サポートされているフォーマット：

  * "*.sg": pdelib sgファイル。フォーマットのバージョン：

      * `format=v"2.0"`: 不要なデータを含む長いバージョン
      * `format=v"2.1"`: セル、セルノード、セル領域、境界ノード、境界領域のみの短縮版
      * `format=v"2.2"`: 2.1のように、セルとノードのパーティショニングに関する追加情報を含む。エッジのパーティショニングはファイルに保存されず、[`induce_edge_partitioning!`](@ref)によって再構築される可能性があります。
  * "*.geo": gmshジオメトリ記述（`using Gmsh`が必要）
  * "*.msh": gmshメッシュ（`using Gmsh`が必要）
