```
gmsh_do_nodes(raw_Nodes) -> NamedTuple
```

[`load_gmsh_file`](@ref)によって作成された`raw_Nodes`を分割します。非パラメトリック曲線のみで動作します。

# 引数

  * `raw_Nodes`: gmshファイル内のノードに関するデータ、

# キーワード

# 戻り値

  * `NamedTuple`: 各次元のための1つの`Dict{Int,String}`、`entityTag => physicalTag`:

      * nodeTag::Array{Int64,1},
      * vx::Array{Float64,1},
      * vy::Array{Float64,1},
      * vz::Array{Float64,1}.

# 例外
