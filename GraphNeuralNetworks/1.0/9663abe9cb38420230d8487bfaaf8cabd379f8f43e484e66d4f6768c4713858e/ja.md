```
SGConv(int => out, k=1; [bias, init, add_self_loops, use_edge_weight])
```

SGCレイヤーは [Simplifying Graph Convolutional Networks](https://arxiv.org/pdf/1902.07153.pdf) からのもので、次の操作を実行します。

$$
H^{K} = (\tilde{D}^{-1/2} \tilde{A} \tilde{D}^{-1/2})^K X \Theta
$$

ここで、$\tilde{A}$ は $A + I$ です。

# 引数

  * `in`: 入力特徴量の数。
  * `out`: 出力特徴量の数。
  * `k` : ホップの数 k。デフォルトは `1`。
  * `bias`: 学習可能なバイアスを追加します。デフォルトは `true`。
  * `init`: 重みの初期化方法。デフォルトは `glorot_uniform`。
  * `add_self_loops`: 畳み込みを行う前にグラフに自己ループを追加します。デフォルトは `false`。
  * `use_edge_weight`: `true` の場合、入力グラフのエッジ重みを考慮します（利用可能な場合）。`add_self_loops=true` の場合、新しい重みは 1 に設定されます。デフォルトは `false`。

# 例

```julia
# データを作成
s = [1,1,2,3]
t = [2,3,1,1]
g = GNNGraph(s, t)
x = randn(Float32, 3, g.num_nodes)

# レイヤーを作成
l = SGConv(3 => 5; add_self_loops = true) 

# フォワードパス
y = l(g, x)       # サイズ:  5 × num_nodes

# エッジ重みを使った畳み込み
w = [1.1, 0.1, 2.3, 0.5]
y = l(g, x, w)

# エッジ重みはグラフに埋め込むこともできます。
g = GNNGraph(s, t, w)
l = SGConv(3 => 5, add_self_loops = true, use_edge_weight=true) 
y = l(g, x) # l(g, x, w) と同じ 
```
