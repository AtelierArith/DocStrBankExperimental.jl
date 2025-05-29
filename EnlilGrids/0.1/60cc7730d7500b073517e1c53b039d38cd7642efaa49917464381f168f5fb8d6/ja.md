```
load_gmsh(filename::AbstractString) -> NamedTuple
```

`filename`をASCIIモードのgmshファイルフォーマットスタイルに従って、別々の`Dict`に読み込みます。

# 引数

  * `filename::AbstractString`: 読み込むファイルの名前、

# キーワード

# 戻り値

  * `NamedTuple`: gmshファイルは`Dict`に分けられます：

      * physicalTagtoName - [`gmsh_do_physicalnames`](@ref)を参照、
      * tagToPhysicalTag - [`gmsh_do_entities`](@ref)を参照、
      * nodes - [`gmsh_do_nodes`](@ref)を参照、
      * elements - [`gmsh_do_elements`](@ref)を参照。

# 例外
