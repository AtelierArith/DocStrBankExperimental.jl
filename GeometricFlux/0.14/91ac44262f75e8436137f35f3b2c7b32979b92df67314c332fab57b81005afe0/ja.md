```
SAGEConv(in => out, σ=identity, aggr=mean; normalize=true, project=false,
         bias=true, num_sample=10, init=glorot_uniform)
```

GraphSAGEネットワークのためのサンプルおよび集約畳み込み層。

# 引数

  * `in`: 入力特徴の次元。
  * `out`: 出力特徴の次元。
  * `σ`: 活性化関数。
  * `aggr`: メッセージ関数の結果に適用される集約関数。`mean`、`max`、

`LSTM`および`GCNConv`が利用可能です。

  * `normalize::Bool`: すべてのノードにわたって特徴を正規化するかどうか。
  * `project::Bool`: 集約の前に投影するかどうか、すなわち`Dense(in, in)`。
  * `bias`: 学習可能なバイアスを追加。
  * `num_sample::Int`: 各ノードがその隣接ノードから取得するサンプルの数。
  * `init`: 重みの初期化子。

# 例

```jldoctest
julia> SAGEConv(1024=>256, relu)
SAGEConv(1024 => 256, relu, aggr=mean, normalize=true, #sample=10)

julia> SAGEConv(1024=>256, relu, num_sample=5)
SAGEConv(1024 => 256, relu, aggr=mean, normalize=true, #sample=5)

julia> MeanAggregator(1024=>256, relu, normalize=false)
SAGEConv(1024 => 256, relu, aggr=mean, normalize=false, #sample=10)

julia> MeanPoolAggregator(1024=>256, relu)
SAGEConv(1024 => 256, relu, project=Dense(1024 => 1024), aggr=mean, normalize=true, #sample=10)

julia> MaxPoolAggregator(1024=>256, relu)
SAGEConv(1024 => 256, relu, project=Dense(1024 => 1024), aggr=max, normalize=true, #sample=10)

julia> LSTMAggregator(1024=>256, relu)
SAGEConv(1024 => 256, relu, aggr=LSTMCell(1024 => 1024), normalize=true, #sample=10)
```

静的グラフでのトレーニング層については[`WithGraph`](@ref)を、[`MeanAggregator`](@ref)、[`MeanPoolAggregator`](@ref)、[`MaxPoolAggregator`](@ref)、および[`LSTMAggregator`](@ref)を参照してください。
