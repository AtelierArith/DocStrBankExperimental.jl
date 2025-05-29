```
get_correction_vertices(resource::MBQCResourceState, vertex::Int64)
```

与えられた頂点に対するMBQCリソース状態の補正を返します。

# 引数

  * `resource::MBQCResourceState`: MBQCリソース状態。
  * `vertex::Int64`: 補正を取得するための頂点。

# 戻り値

  * `corrections`: XおよびZ補正を含むタプル。

# 例

```julia
corrections = get_correction_vertices(resource, vertex) # 与えられた頂点に必要な補正を返します
```
