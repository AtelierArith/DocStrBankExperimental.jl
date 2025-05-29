```
periphery(g, distmx=weights(g))
periphery(all_ecc)
```

グラフの直径に等しい偏心度を持つすべての頂点の集合を返します（つまり、最大の偏心度を持つ頂点の集合です）。

最終的に、各ノードの偏心度を含むベクトル `all_ecc` を引数として渡すことができます。

[`eccentricities`](@ref) を参照してください。
