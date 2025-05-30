```
centrality(::Type{ClosenessCentrality}, N::SpeciesInteractionNetwork{<:Unipartite, <:Probabilistic})
```

確率的ネットワークの近接中心性は、*ランダムウォーク*近接中心性を使用して測定され、ノードiから始まるランダムウォークのノードjへの最初の通過時間として、2つのノードiとjの間の距離が測定されます。この関数は最短経路を探さないため、比較的速いです。
