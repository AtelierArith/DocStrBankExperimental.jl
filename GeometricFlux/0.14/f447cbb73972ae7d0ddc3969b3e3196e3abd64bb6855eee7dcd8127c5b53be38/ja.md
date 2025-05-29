```
EdgeConv(nn; aggr=max)
```

エッジ畳み込み層。

# 引数

  * `nn`: ニューラルネットワーク（例：Dense層またはMLP）。
  * `aggr`: メッセージ関数の結果に適用される集約関数。

`+`、`max`、および`mean`が利用可能です。

# 例

```jldoctest
julia> EdgeConv(Dense(1024, 256, relu))
EdgeConv(Dense(1024 => 256, relu), aggr=max)

julia> EdgeConv(Dense(1024, 256, relu), aggr=+)
EdgeConv(Dense(1024 => 256, relu), aggr=+)
```

静的グラフでのトレーニング層については、[`WithGraph`](@ref)も参照してください。
