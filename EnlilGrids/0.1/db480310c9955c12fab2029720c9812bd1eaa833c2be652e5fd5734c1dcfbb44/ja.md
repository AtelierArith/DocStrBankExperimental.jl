```
gmsh_do_physicalnames(raw_PhysicalNames) -> NamedTuple
```

[`load_gmsh_file`](@ref) によって作成された `raw_PhysicalNames` を次元ごとに1つの `Dict` に分割します。

# 引数

  * `raw_PhysicalNames`: gmshファイル内の物理名に関するデータ、

# キーワード

# 戻り値

  * `NamedTuple`: 各次元のための1つの `Dict{Int,String}`、`physicalTag => Name`:

      * physicalTag1DtoName,
      * physicalTag2DtoName,
      * physicalTag3DtoName.

# 例外
