```
GConvGRUCell(in => out, k; [bias, init])
```

グラフ畳み込みゲート付き再帰ユニット (GConvGRU) 再帰セルは、論文 [Structured Sequence Modeling with Graph Convolutional Recurrent Networks](https://arxiv.org/abs/1612.07659) に基づいています。

空間的依存関係をモデル化するために [`ChebConv`](@ref) を使用し、その後、時間的依存関係をモデル化するためにゲート付き再帰ユニット (GRU) セルを使用します。

# 引数

  * `in => out`: `in` は入力ノード特徴の数、`out` は出力ノード特徴の数を表すペアです。
  * `k`: チェビシェフ多項式の次数。
  * `bias`: 学習可能なバイアスを追加します。デフォルトは `true` です。
  * `init`: 重みの初期化子。デフォルトは `glorot_uniform` です。

# フォワード

```
cell(g::GNNGraph, x, [h])
```

  * `g`: 入力グラフ。
  * `x`: ノード特徴。サイズは `in x num_nodes` の行列である必要があります。
  * `h`: GRUセルの現在の隠れ状態。与えられた場合、サイズは `out x num_nodes` の行列です。提供されない場合は、ゼロの行列であると仮定されます。

1回の再帰ステップを実行し、タプル `(h, h)` を返します。ここで `h` は GRUセルの更新された隠れ状態です。

# 例

```jldoctest
julia> using GraphNeuralNetworks, Flux

julia> num_nodes, num_edges = 5, 10;

julia> d_in, d_out = 2, 3;

julia> timesteps = 5;

julia> g = rand_graph(num_nodes, num_edges);

julia> x = [rand(Float32, d_in, num_nodes) for t in 1:timesteps];

julia> cell = GConvGRUCell(d_in => d_out, 2);

julia> state = Flux.initialstates(cell);

julia> y = state;

julia> for xt in x
           y, state = cell(g, xt, state)
       end

julia> size(y) # (d_out, num_nodes)
(3, 5)
```
