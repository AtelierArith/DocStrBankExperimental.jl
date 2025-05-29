```
DCGRUCell(in => out, k; [bias, init])
```

論文 [Diffusion Convolutional Recurrent Neural Network: Data-driven Traffic Forecasting](https://arxiv.org/abs/1707.01926) からの拡散畳み込み再帰ニューラルネットワーク (DCGRU) セルです。

空間的依存関係をモデル化するために [`DConv`](@ref) レイヤーを適用し、時間的依存関係をモデル化するためにゲート付き再帰ユニット (GRU) セルを組み合わせています。

# 引数

  * `in`: 入力ノード特徴の数。
  * `out`: 出力ノード特徴の数。
  * `k`: `DConv` の拡散ステップ。
  * `bias`: 学習可能なバイアスを追加します。デフォルトは `true` です。
  * `init`: 畳み込み重みの初期化子。デフォルトは `glorot_uniform` です。

# フォワード

```
cell(g::GNNGraph, x, [h])
```

  * `g`: 入力グラフ。
  * `x`: ノード特徴。サイズ `in x num_nodes` の行列である必要があります。
  * `h`: GRU セルの現在の状態。サイズ `out x num_nodes` の行列です。提供されない場合は、ゼロの行列であると見なされます。

1 回の再帰ステップを実行し、更新された GRU セルの隠れ状態 `h` を含むタプル `(h, h)` を返します。

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
