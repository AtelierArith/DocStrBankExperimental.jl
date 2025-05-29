```
dorogovtsev_mendes(n)
```

Dorogovtsev-Mendes法によってランダムな`n`頂点グラフを生成します（`n \ge 3`）。

Dorogovtsev-Mendesプロセスは三角形グラフから始まり、`n-3`の追加頂点を挿入します。頂点が追加されるたびに、ランダムな辺が選択され、新しい頂点が選ばれた辺の2つの端点に接続されます。これにより、多くの三角形と高い局所クラスタリング係数を持つグラフが生成されます。

頂点が追加されるにつれてグラフの進化を追跡することがしばしば有用です。このアルゴリズムの`t`番目の段階からグラフにアクセスするには、`g[1:t]`を使用して最初の`t`頂点にアクセスできます。

### 参考文献

  * http://graphstream-project.org/doc/Generators/Dorogovtsev-Mendes-generator/
  * https://arxiv.org/pdf/cond-mat/0106144.pdf#page=24

# 例

```jldoctest
julia> dorogovtsev_mendes(10)
{10, 17} undirected simple Int64 graph

julia> dorogovtsev_mendes(11, seed=123)
{11, 19} undirected simple Int64 graph
```
