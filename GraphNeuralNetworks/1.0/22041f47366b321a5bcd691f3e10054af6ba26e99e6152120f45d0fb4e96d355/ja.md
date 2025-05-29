```
TGCNCell(in => out; kws...)
```

論文 [T-GCN: A Temporal Graph Convolutional Network for Traffic Prediction](https://arxiv.org/pdf/1811.05320) に基づく再帰的グラフ畳み込みセル。

空間的依存関係をモデル化するために2つのスタックされた [`GCNConv`](@ref) レイヤーを使用し、時間的依存関係をモデル化するためにGRUメカニズムを使用します。

`in` と `out` はそれぞれ入力および出力ノード特徴の数です。キーワード引数は [`GCNConv`](@ref) コンストラクタに渡されます。

# フォワード

```
cell(g::GNNGraph, x, [state])
```

  * `g`: 入力グラフ。
  * `x`: ノード特徴。サイズ `in x num_nodes` の行列である必要があります。
  * `state`: セルの現在の状態。提供されない場合は、`Flux.initialstates(cell)` を呼び出すことで生成されます。状態はサイズ `out x num_nodes` の行列です。

更新されたノード特徴と更新された状態を返します。

# 例

```jldoctest
julia> using GraphNeuralNetworks, Flux

julia> num_nodes, num_edges = 5, 10;

julia> d_in, d_out = 2, 3;

julia> timesteps = 5;

julia> g = rand_graph(num_nodes, num_edges);

julia> x = [rand(Float32, d_in, num_nodes) for t in 1:timesteps];

julia> cell = DCGRUCell(d_in => d_out, 2);

julia> state = Flux.initialstates(cell);

julia> y = state;

julia> for xt in x
           y, state = cell(g, xt, state)
       end

julia> size(y) # (d_out, num_nodes)
(3, 5)
```
