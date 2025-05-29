```
get_output_size(resource::MBQCResourceState)::Int64
```

与えられた `MBQCResourceState` の出力サイズを取得します。

# 引数

  * `resource::MBQCResourceState`: 出力サイズを取得するためのリソース状態。

# 戻り値

  * `Int64`: 出力のサイズ。

# 例

```julia
size = get_output_size(resource) # 出力のサイズを返します
```
