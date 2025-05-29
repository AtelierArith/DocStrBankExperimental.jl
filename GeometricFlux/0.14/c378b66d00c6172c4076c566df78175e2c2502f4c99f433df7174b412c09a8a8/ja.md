```
GatedGraphConv([fg,] out, num_layers; aggr=+, init=glorot_uniform)
```

ゲーテッドグラフ畳み込み層。

# 引数

  * `out`: 出力特徴の次元。
  * `num_layers`: ゲーテッドリカレントユニットの数。
  * `aggr`: メッセージ関数の結果に適用される集約関数。`+`、`-`、

`*`、`/`、`max`、`min`、および `mean` が利用可能です。

# 例

```jldoctest
julia> GatedGraphConv(256, 4)
GatedGraphConv((256 => 256)^4, aggr=+)

julia> GatedGraphConv(256, 4, aggr=*)
GatedGraphConv((256 => 256)^4, aggr=*)
```

静的グラフでのトレーニング層については、[`WithGraph`](@ref)を参照してください。
