```
hom_tensor(G::FinGenAbGroup, H::FinGenAbGroup, A::Vector{ <: Map{FinGenAbGroup, FinGenAbGroup}}) -> Map
```

群 $G = G_1 \otimes \cdots \otimes G_n$ と $H = H_1 \otimes \cdots \otimes H_n$ および写像 $\phi_i: G_i\to H_i$ が与えられたとき、写像のテンソル積を計算します。
