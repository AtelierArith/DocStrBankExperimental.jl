```
gmsh_do_elements(raw_Elements) -> NamedTuple
```

[`load_gmsh_file`](@ref)によって作成された`raw_Elements`を分割します。

# 引数

  * `raw_Elements`: gmshファイル内の要素に関するデータ、

# キーワード

# 戻り値

  * `NamedTuple`: 各次元に対して1つの`Dict{Int,String}`、`entityTag => physicalTag`:

      * entityTag1D   :: Array{Int64,1},
      * entityTag2D   :: Array{Int64,1},
      * entityTag3D   :: Array{Int64,1},
      * elementType1D :: Array{Int64,1},
      * elementType2D :: Array{Int64,1},
      * elementType3D :: Array{Int64,1},
      * elementTag1D  :: Array{Int64,1},
      * elementTag2D  :: Array{Int64,1},
      * elementTag3D  :: Array{Int64,1},
      * nodeTags1D    :: Array{Array{Int64,1},1},
      * nodeTags2D    :: Array{Array{Int64,1},1},
      * nodeTags3D    :: Array{Array{Int64,1},1}.

# 例外
