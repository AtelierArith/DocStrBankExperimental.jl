```
GNNRecurrence(cell)
```

グラフ再帰 `cell` を適用して、ノード特徴の全時系列を一度に処理する再帰層を構築します。

`cell` は、フォワードパスのために次のインターフェースを満たす必要があります: `yt, state = cell(g, xt, state)`、ここで `xt` は入力ノード特徴、`yt` は更新されたノード特徴、`state` は更新されるセル状態です。

# フォワード

```
layer(g, x, [state])
```

入力シーケンスの各タイムステップに再帰セルを適用します。

## 引数

  * `g`: 入力 `GNNGraph` または `TemporalSnapshotsGNNGraph`。

      * `GNNGraph` の場合、すべてのタイムステップで同じグラフが使用されます。
      * `TemporalSnapshotsGNNGraph` の場合、各タイムステップで異なるグラフが使用されます。すべてのセルがこれをサポートしているわけではありません。
  * `x`: 時間変化するノード特徴。 

      * `g` が `GNNGraph` の場合、サイズ `in x timesteps x num_nodes` の配列です。
      * `g` が `TemporalSnapshotsGNNGraph` の場合、長さ `timesteps` のベクトルで、要素 `t` はサイズ `in x num_nodes_t` です。
  * `state`: セルの初期状態。提供されない場合は、`Flux.initialstates(cell)` を呼び出して生成されます。

## 戻り値

更新されたノード特徴を返します：

  * `g` が `GNNGraph` の場合、サイズ `out_features x timesteps x num_nodes` の配列を返します。
  * `g` が `TemporalSnapshotsGNNGraph` の場合、長さ `timesteps` のベクトルを返し、要素 `t` はサイズ `out_features x num_nodes_t` です。

# 例

以下の例では、静的グラフと時間変化するノード特徴を考慮します。

```jldoctest
julia> num_nodes, num_edges = 5, 10;

julia> d_in, d_out = 2, 3;

julia> timesteps = 5;

julia> g = rand_graph(num_nodes, num_edges);
GNNGraph:
  num_nodes: 5
  num_edges: 10

julia> x = rand(Float32, d_in, timesteps, num_nodes);

julia> cell = GConvLSTMCell(d_in => d_out, 2)
GConvLSTMCell(2 => 3, 2)  # 168 parameters

julia> layer = GNNRecurrence(cell)
GNNRecurrence(
  GConvLSTMCell(2 => 3, 2),             # 168 parameters
)                   # Total: 24 arrays, 168 parameters, 2.023 KiB.

julia> y = layer(g, x);

julia> size(y) # (d_out, timesteps, num_nodes)
(3, 5, 5)
```

次に、時間変化するグラフと時間変化するノード特徴を考慮します。

```jldoctest
julia> d_in, d_out = 2, 3;

julia> timesteps = 5;

julia> num_nodes = [10, 10, 10, 10, 10];

julia> num_edges = [10, 12, 14, 16, 18];

julia> snapshots = [rand_graph(n, m) for (n, m) in zip(num_nodes, num_edges)];

julia> tg = TemporalSnapshotsGNNGraph(snapshots)

julia> x = [rand(Float32, d_in, n) for n in num_nodes];

julia> cell = EvolveGCNOCell(d_in => d_out)
EvolveGCNOCell(2 => 3)  # 321 parameters

julia> layer = GNNRecurrence(cell)
GNNRecurrence(
  EvolveGCNOCell(2 => 3),               # 321 parameters
)                   # Total: 5 arrays, 321 parameters, 1.535 KiB.

julia> y = layer(tg, x);

julia> length(y)    # timesteps
5

julia> size(y[end]) # (d_out, num_nodes[end])
(3, 10)
```
