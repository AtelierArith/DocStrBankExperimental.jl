```
load_gmsh_file(filename::AbstractString) -> NamedTuple
```

`filename`をASCIIモードのgmshファイル形式スタイルに従って別々の配列に読み込みます。

# 引数

  * `filename::AbstractString`: 読み込むファイルの名前、

# キーワード

# 戻り値

  * `NamedTuple`: gmshファイルは部分文字列の配列に分けられます：

      * msh_version - gmshファイルのバージョンに関する情報を含む、
      * msh_PhysicalNames - 物理オブジェクトに関するデータを含む、
      * msh_Entities - エンティティに関するデータを含む、
      * msh_Nodes - 座標を含むノードに関するデータを含む、
      * msh_Elements - 要素に関するデータを含む、

# 例外

  * `Error`: 名前が`filename`のファイルは存在しません、
  * `Error`: 名前が`filename`のファイルはバイナリモードで保存されています。
