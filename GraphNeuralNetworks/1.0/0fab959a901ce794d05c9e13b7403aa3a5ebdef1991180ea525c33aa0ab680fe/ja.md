```
TAGConv(in => out, k=3; bias=true, init=glorot_uniform, add_self_loops=true, use_edge_weight=false)
```

[Topology Adaptive Graph Convolutional Networks](https://arxiv.org/pdf/1710.10370.pdf)からのTAGConvレイヤー。このレイヤーは、データのトポロジーに適応するフィルターを適用することによってグラフ畳み込みのアイデアを拡張します。次の操作を実行します：

$$
H^{K} = {\sum}_{k=0}^K (D^{-1/2} A D^{-1/2})^{k} X {\Theta}_{k}
$$

ここで、`A`はグラフの隣接行列、`D`は次数行列、`X`は入力特徴行列、${\Theta}_{k}$は各ホップ`k`に対するユニークな重み行列です。

# 引数

  * `in`: 入力特徴の数。
  * `out`: 出力特徴の数。
  * `k`: 考慮する最大ホップ数。デフォルトは`3`です。
  * `bias`: 学習可能なバイアス項を含めるかどうか。デフォルトは`true`です。
  * `init`: 重みの初期化関数。デフォルトは`glorot_uniform`です。
  * `add_self_loops`: 隣接行列に自己ループを追加するかどうか。デフォルトは`true`です。
  * `use_edge_weight`: `true`の場合、計算にエッジの重みが考慮されます（利用可能な場合）。デフォルトは`false`です。

# 例

```julia
# 例のグラフデータ
s = [1, 1, 2, 3]
t = [2, 3, 1, 1]
g = GNNGraph(s, t)  # グラフを作成
x = randn(Float32, 3, g.num_nodes)  # 各ノードのランダムな特徴

# TAGConvレイヤーを作成
l = TAGConv(3 => 5, k=3; add_self_loops=true)

# TAGConvレイヤーを適用
y = l(g, x)  # 出力サイズ: 5 × num_nodes
```
