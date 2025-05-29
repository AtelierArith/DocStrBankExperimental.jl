```
get_size_measurement_vector(resource::MBQCResourceState)::Int64
```

与えられた `MBQCResourceState` の測定ベクトルのサイズを取得します。

# 引数

  * `resource::MBQCResourceState`: 測定ベクトルのサイズを計算するためのリソース状態。

# 戻り値

  * `Int64`: 測定ベクトルのサイズ。

# 例

```julia
size = get_size_measurement_vector(resource) # 測定ベクトルのサイズを返します
```
