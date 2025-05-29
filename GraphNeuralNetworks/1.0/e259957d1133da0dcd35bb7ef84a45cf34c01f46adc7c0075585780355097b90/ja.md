```
     EvolveGCNOCell(in => out; bias = true, init = glorot_uniform)

論文 [EvolveGCN: Evolving Graph Convolutional Networks for Dynamic Graphs](https://arxiv.org/abs/1902.10191) に基づく "-O" 型の進化グラフ畳み込みネットワークセル。

空間的依存関係をモデル化するために [`GCNConv`](@ref) レイヤーを使用し、時間的依存関係をモデル化するために `LSTMCell` を使用します。時間変化するグラフとノード特徴に対応できます。

# 引数

  * `in => out`: `in` は入力ノード特徴の数、`out` は出力ノード特徴の数を表すペアです。
  * `bias`: 畳み込みとLSTMセルのための学習可能なバイアスを追加します。デフォルトは `true` です。
  * `init`: 畳み込みのための重みの初期化子。デフォルトは `glorot_uniform` です。

# フォワード

```

cell(g::GNNGraph, x, [state]) -> x, state

```

  * `g`: 入力グラフ。
  * `x`: ノード特徴。サイズは `in x num_nodes` の行列である必要があります。
  * `state`: セルの現在の状態。状態は `(weight, lstm)` というタプルで、`weight` は畳み込みの重み、`lstm` はLSTMの状態です。提供されない場合は、`Flux.initialstates(cell)` を呼び出すことで生成されます。

更新されたノード特徴 `x` と更新された状態を返します。

```

jldoctest julia> using GraphNeuralNetworks, Flux

julia> num*nodes, num*edges = 5, 10;

julia> d*in, d*out = 2, 3;

julia> timesteps = 5;

julia> g = [rand*graph(num*nodes, num_edges) for t in 1:timesteps];

julia> x = [rand(Float32, d*in, num*nodes) for t in 1:timesteps];

julia> cell1 = EvolveGCNOCell(d*in => d*out) EvolveGCNOCell(2 => 3)  # 321 parameters

julia> cell2 = EvolveGCNOCell(d*out => d*out) EvolveGCNOCell(3 => 3)  # 696 parameters

julia> state1 = Flux.initialstates(cell1);

julia> state2 = Flux.initialstates(cell2);

julia> outputs = [];

julia> for t in 1:timesteps            zt, state1 = cell1(g[t], x[t], state1)            yt, state2 = cell2(g[t], zt, state2)            outputs = vcat(outputs, [yt])        end

julia> size(outputs[end]) # (d*out, num*nodes) (3, 5) ```
