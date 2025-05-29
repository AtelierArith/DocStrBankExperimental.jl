```
get_stop_start_vertices(resource::MBQCResourceState)
```

与えられた `MBQCResourceState` の開始および停止頂点を取得します。

# 引数

  * `resource::MBQCResourceState`: MBQCリソース状態。

# 戻り値

  * `Tuple{Int64, Int64}`: 開始および停止頂点を含むタプル。

# 例

```julia
start, stop = get_stop_start_vertices(resource) # 開始および停止頂点を返します
```
