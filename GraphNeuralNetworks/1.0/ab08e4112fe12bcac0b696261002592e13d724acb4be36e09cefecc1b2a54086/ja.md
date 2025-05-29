```
GConvLSTMCell(in => out, k; [bias, init])
```

論文 [Structured Sequence Modeling with Graph Convolutional Recurrent Networks](https://arxiv.org/abs/1612.07659) に基づくグラフ畳み込みLSTM再帰セル。

空間的依存関係をモデル化するために [`ChebConv`](@ref) を使用し、その後に時間的依存関係をモデル化するために長短期記憶（LSTM）セルを使用します。

# 引数

  * `in => out`: `in` が入力ノード特徴の数で、`out` が出力ノード特徴の数であるペア。
  * `k`: チェビシェフ多項式の次数。
  * `bias`: 学習可能なバイアスを追加します。デフォルトは `true`。
  * `init`: 重みの初期化子。デフォルトは `glorot_uniform`。

# フォワード

```
cell(g::GNNGraph, x, [state])
```

  * `g`: 入力グラフ。
  * `x`: ノード特徴。サイズ `in x num_nodes` の行列である必要があります。
  * `state`: LSTMセルの現在の状態。与えられた場合、これは `(h, c)` のタプルであり、`h` と `c` はどちらもサイズ `out x num_nodes` の配列です。提供されない場合は、ゼロの行列のタプルであると見なされます。

1回の再帰ステップを実行し、更新された隠れ状態 `h` のタプル `(output, state)` を返します。ここで、`output` はLSTMセルの更新された隠れ状態 `h` であり、`state` は更新されたタプル `(h, c)` です。

# 例

```jldoctest
julia> using GraphNeuralNetworks, Flux

julia> num_nodes, num_edges = 5, 10;

julia> d_in, d_out = 2, 3;

julia> timesteps = 5;

julia> g = rand_graph(num_nodes, num_edges);

julia> x = [rand(Float32, d_in, num_nodes) for t in 1:timesteps];

julia> cell = GConvLSTMCell(d_in => d_out, 2);

julia> state = Flux.initialstates(cell);

julia> y = state[1];

julia> for xt in x
           y, state = cell(g, xt, state)
       end

julia> size(y) # (d_out, num_nodes)
(3, 5)
```
