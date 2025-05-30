```
lancichinetti_fortunato_radicchi(n::Integer, k_avg::Integer, k_max::Integer)
```

`n` 頂点、`k_avg` 平均次数、`k_max` 最大次数を持つ [Lancichinetti-Fortunato-Radicchi モデル](https://en.wikipedia.org/wiki/Lancichinetti-Fortunato-Radicchi_benchmark) のランダムグラフを作成します。このモデルは、べき法則の次数分布とコミュニティ構造を持つグラフを生成します。抽象的には、コミュニティサイズと次数分布のべき法則分布を持つ SBM と考えることができます。

### オプション引数

  * `mixing_parameter`: 混合パラメータ μ、{外部次数}/{総次数} の平均比を定義します。
  * `is_directed=false`: true の場合、向き付きグラフを返します。
  * `seed=1`: ランダムシードを設定します。
  * `tau=2.0`: 次数分布のべき法則分布の指数。
  * `tau2=1.0`: コミュニティサイズ分布のべき法則分布の指数。
  * `nmin=nothing`, `nmax=nothing`: コミュニティサイズの最小値と最大値（範囲）。
  * `overlapping_nodes=0`: 重複ノードの数。
  * `overlap_membership=0`: 重複ノードのメンバーシップの数。
  * `clustering_coeff=nothing`: 指定された場合、プログラムは平均クラスタ係数を希望の値まで増加させるために再配線を行います。

### その他のオプション

外部次数/総次数の比率の分布が混合パラメータによって上限（下限）で制約されるベンチマークを生成したい場合は、これらのオプションのいずれかを使用します。言い換えれば、これらのオプションのいずれかを使用すると、混合パラメータは外部次数/総次数の平均比（従来のように）ではなく、その分布の最大（または最小）になります。これらのオプションを使用する際、プログラムが本質的に行うのは、外部次数を常に超過（または不足）で近似し、必要に応じて次数分布を修正することです。それでも、この最後の可能性はごく少数のノードに対して発生し、数値シミュレーションはそれが次数分布に著しく影響を与えないことを示しています。

  * `excess=false`: true の場合、次数分布は μ によって上限が設定されます。
  * `defect=false`: true の場合、次数分布は μ によって下限が設定されます。

!!! warning "超過および不足オプションの使用"
    `excess` と `defect` の両方のオプションは同時に `true` にはできません


### 注意事項

入力パラメータの組み合わせによっては、関数が解に収束しない場合があります。この場合は、異なる入力パラメータを試してください。

### 参考文献

  * 重複コミュニティを持つ向き付きおよび重み付きグラフにおけるコミュニティ検出アルゴリズムのテストのためのベンチマーク、Andrea Lancichinetti と Santo Fortunato、2009年。 [https://doi.org/10.1103/PhysRevE.80.016118](https://doi.org/10.1103/PhysRevE.80.016118)
  * コミュニティ検出アルゴリズムのテストのためのベンチマークグラフ、Andrea Lancichinetti、Santo Fortunato、Filippo Radicchi、2008年。 [https://doi.org/10.1103/PhysRevE.78.046110](https://doi.org/10.1103/PhysRevE.78.046110)
  * [著者によるオリジナルソースコードへのリンク](https://sites.google.com/site/andrealancichinetti/benchmarks?authuser=0)

## 例

```jldoctest
julia> using LFRBenchmarkGraphs

julia> g,cid = lancichinetti_fortunato_radicchi(20, 4, 5);

julia> g
{20, 35} undirected simple Int64 graph

julia> println(cid)  # コミュニティラベル
[1, 1, 3, 2, 3, 2, 1, 2, 1, 1, 1, 3, 1, 3, 2, 3, 3, 1, 2, 3]

```
