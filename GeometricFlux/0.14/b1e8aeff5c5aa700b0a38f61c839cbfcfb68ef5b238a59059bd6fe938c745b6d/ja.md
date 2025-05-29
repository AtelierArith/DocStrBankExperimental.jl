```
WithGraph([g], layer; dynamic=nothing)
```

静的グラフでGNNレイヤーをトレーニングします。

# 引数

  * `g`: `FeaturedGraph`が与えられた場合、固定グラフがトレーニングに使用されます。
  * `layer`: GNNレイヤー。
  * `dynamic`: 関数が与えられた場合、レイヤー内で与えられた関数を通じて動的グラフを構築することにより、動的グラフの更新を有効にします。

# 例

```jldoctest
julia> using GraphSignals, GeometricFlux

julia> adj = [0 1 0 1;
              1 0 1 0;
              0 1 0 1;
              1 0 1 0];

julia> fg = FeaturedGraph(adj);

julia> gc = WithGraph(fg, GCNConv(1024=>256))  # 自己ループを追加して前処理されたグラフ
WithGraph(Graph(#V=4, #E=8), GCNConv(1024 => 256))

julia> WithGraph(fg, Dense(10, 5))
Dense(10 => 5)      # 55 パラメータ

julia> model = Chain(
           GCNConv(32=>32),
           gc,
       );

julia> WithGraph(fg, model)
Chain(
  WithGraph(
    GCNConv(32 => 32),                  # 1_056 パラメータ
  ),
  WithGraph(
    GCNConv(1024 => 256),               # 262_400 パラメータ
  ),
)         # 合計: 4 つのトレーニング可能な配列、263_456 パラメータ、
          # さらに 2 つのトレーニング不可能な、32 パラメータ、サマリーサイズ 1.006 MiB.
```
