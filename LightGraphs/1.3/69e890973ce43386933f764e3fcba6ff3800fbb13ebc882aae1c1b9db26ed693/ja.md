```
modularity(g, c, distmx=weights(g), γ=1.0)
```

与えられた分割ベクトル `c` に対して、無向および有向グラフ `g` のニューマンのモジュラリティ `Q` を表す値を返します。このメソッドは、距離行列が提供されている場合、重み付きグラフもサポートしています。

無向グラフのモジュラリティ $Q$:

$$
Q = \frac{1}{2m} \sum_{c} \left( e_{c} - \gamma \frac{K_c^2}{2m} \right)
$$

有向グラフのモジュラリティ $Q$:

$$
Q = \frac{1}{m} \sum_{c} \left( e_{c} - \gamma \frac{K_c^{in} K_c^{out}}{m} \right)
$$

ここで:

  * $$
    m
    $$

    : ネットワーク内のエッジの総数
  * $$
    e_c
    $$

    : コミュニティ $c$ 内のエッジの数
  * $$
    K_c
    $$

    : コミュニティ $c$ 内のノードの次数の合計、またはグラフが重み付きの場合はコミュニティ $c$ 内のノードの重み付き次数の合計。$K_c^{in}$ はコミュニティ $c$ 内のノードの入次数の合計です。

### オプション引数

  * `distmx=weights(g)`: 重み付きグラフのための距離行列
  * `γ=1.0`: `γ > 0` は解像度パラメータです。モジュラリティがネットワーク内のコミュニティ構造を見つけるために使用されるとき（すなわち、[ルーヴァン法によるコミュニティ検出](https://en.wikipedia.org/wiki/Louvain_Modularity)）、高い解像度はより多くのコミュニティをもたらし、低い解像度はより少ないコミュニティをもたらします。`γ=1.0` の場合、モジュラリティの従来の定義につながります。

### 参考文献

  * M. E. J. Newman と M. Girvan. "ネットワークにおけるコミュニティ構造の発見と評価". Phys. Rev. E 69, 026113 (2004). [(arXiv)](https://arxiv.org/abs/cond-mat/0308217)
  * J. Reichardt と S. Bornholdt. "コミュニティ検出の統計力学". Phys. Rev. E 74, 016110 (2006). [(arXiv)](https://arxiv.org/abs/cond-mat/0603718)
  * E. A. Leicht と M. E. J. Newman. "有向ネットワークにおけるコミュニティ構造". Physical Review Letter, 100:118703, (2008). [(arXiv)](https://arxiv.org/pdf/0709.4500.pdf)

# 例

```jldoctest
julia> using LightGraphs

julia> barbell = blockdiag(complete_graph(3), complete_graph(3));

julia> add_edge!(barbell, 1, 4);

julia> modularity(barbell, [1, 1, 1, 2, 2, 2])
0.35714285714285715

julia> modularity(barbell, [1, 1, 1, 2, 2, 2], γ=0.5)
0.6071428571428571  

julia> using SimpleWeightedGraphs

julia> triangle = SimpleWeightedGraph(3);

julia> add_edge!(triangle, 1, 2, 1);

julia> add_edge!(triangle, 2, 3, 1);

julia> add_edge!(triangle, 3, 1, 1);

julia> barbell = blockdiag(triangle, triangle);

julia> add_edge!(barbell, 1, 4, 5); # このエッジの重みは5です

julia> modularity(barbell, [1, 1, 1, 2, 2, 2])
0.045454545454545456
```
