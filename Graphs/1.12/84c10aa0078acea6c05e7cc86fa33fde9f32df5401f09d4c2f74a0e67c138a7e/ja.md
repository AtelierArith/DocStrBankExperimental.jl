```
assortativity(g)
```

グラフ `g` の[アソートativity係数](https://en.wikipedia.org/wiki/Assortativity)を返します。これは、グラフのすべてのエッジの端点間の過剰次数のピアソン相関として定義されます。

過剰次数は、リンクされた頂点の次数から1を引いた値に等しく、つまりペアをリンクするエッジを考慮しないことを意味します。有向グラフでは、ペアの値はソース頂点の出次数と宛先頂点の入次数です。

# 例

```jldoctest
julia> using Graphs

julia> assortativity(star_graph(4))
-1.0
```
