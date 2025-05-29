```
get_input_size(resource::MBQCResourceState)::Int64
```

与えられた `MBQCResourceState` の入力のサイズを取得します。

# 引数

  * `resource::MBQCResourceState`: MBQC リソース状態。

# 戻り値

  * `Int64`: 入力のサイズ。

# 例

```julia
size = get_input_size(resource) # 入力のサイズを返します
```
