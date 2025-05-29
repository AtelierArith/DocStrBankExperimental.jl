```
hom_direct_sum(G::FinGenAbGroup, H::FinGenAbGroup, A::Matrix{ <: Map{FinGenAbGroup, FinGenAbGroup}}) -> Map
```

群 $G$ と $H$ が直積として作成され、マトリックス $A$ がマップ $A[i,j] : G_i \to H_j$ を含む場合、誘導されたホモモルフィズムを返します。
