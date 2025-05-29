```
centrality(::Type{EigenvectorCentrality}, N::SpeciesInteractionNetwork{<:Unipartite, <:Interactions})
```

固有ベクトル中心性は、ネットワーク内の中心性の合計が1になるように修正されています。

固有ベクトル中心性は、ランダムベクトルから始めて、フォン・ミーゼス反復を使用して計算されます。

ここで、Aはグラフの隣接行列、bは中心性のベクトルです。各反復で、ベクトルはA×b/|A×b|に更新され、|⋅|はノルムです。

反復の回数は変数`SpeciesInteractionNetworks.CENTRALITY_MAXITER`によって決定され、アルゴリズムは通常迅速に収束します。

###### 参考文献

[Landau1895Zur](@citet*)
