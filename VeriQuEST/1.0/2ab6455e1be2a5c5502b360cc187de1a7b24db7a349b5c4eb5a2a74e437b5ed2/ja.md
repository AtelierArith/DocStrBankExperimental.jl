```
get_measurement_outcome_iterator(resource::MBQCResourceState)
```

MBQCリソース状態の頂点を測定するためのインデックスを生成するイテレータを返します。

# 引数

  * `resource::MBQCResourceState`: MBQCリソース状態。

# 返り値

リソース状態の頂点を測定するためのインデックスを生成するイテレータ。

# 例

```julia
iterator = get_measurement_outcome_iterator(resource) # リソースの頂点を測定するためのインデックスを生成するイテレータを返します
```
