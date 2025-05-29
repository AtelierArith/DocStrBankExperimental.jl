```
get_graph(resource::MBQCResourceState)
```

与えられた `MBQCResourceState` に関連付けられたグラフを取得します。

# 引数

  * `resource::MBQCResourceState`: リソース状態オブジェクト。

# 戻り値

  * リソース状態に関連付けられたグラフ。

# 例

```julia
graph = get_graph(resource) # リソースに関連付けられたグラフを返します
```
