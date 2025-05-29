```
GraphConv(in => out, σ=identity, aggr=+; bias=true, init=glorot_uniform)
```

グラフニューラルネットワーク層。

# 引数

  * `in`: 入力特徴の次元。
  * `out`: 出力特徴の次元。
  * `σ`: 活性化関数。
  * `aggr`: メッセージ関数の結果に適用される集約関数。`+`、`-`、

`*`、`/`、`max`、`min`、および `mean` が利用可能です。

  * `bias`: 学習可能なバイアスを追加します。
  * `init`: 重みの初期化子。

# 例

```jldoctest
julia> GraphConv(1024=>256, relu)
GraphConv(1024 => 256, relu, aggr=+)

julia> GraphConv(1024=>256, relu, *)
GraphConv(1024 => 256, relu, aggr=*)
```

静的グラフでのトレーニング層については、[`WithGraph`](@ref)も参照してください。
