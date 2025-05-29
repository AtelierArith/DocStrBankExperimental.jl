```
get_set(data::T) where T<:WiNDCtable  

get_set(data::T, set_name::String) where T<:WiNDCtable

get_set(data::T, set_name::Vector{String}) where T<:WiNDCtable
```

指定されたセットの要素を返します。セットが指定されていない場合は、すべてのセットを返します。

## 必要な引数

1. `data` - WiNDCtableのようなオブジェクト。
2. `set_name` - 抽出するセット名を表す文字列または文字列のベクター。

## 戻り値

`:element`、`:set`、および `:description` の3つの列を持つDataFrameを返します。
