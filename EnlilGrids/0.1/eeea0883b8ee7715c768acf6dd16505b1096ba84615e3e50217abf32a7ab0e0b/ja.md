```
gmsh_do_entities(raw_Entities) -> NamedTuple
```

[`load_gmsh_file`](@ref)によって作成された`raw_Entities`を、エンティティの各タイプごとに1つの`Dict`に分割します。エンティティごとに物理タグは1つのみで動作します。

# 引数

  * `raw_Entities`: gmshファイル内のエンティティに関するデータ、

# キーワード

# 戻り値

  * `NamedTuple`: 各次元ごとに1つの`Dict{Int,String}`、`entityTag => physicalTag`:

      * pointTagtoPhysicalTag,
      * curveTagtoPhysicalTag,
      * surfaceTagtoPhysicalTag,
      * volumeTagtoPhysicalTag.

# 例外
