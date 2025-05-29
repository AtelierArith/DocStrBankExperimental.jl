```
hom_direct_sum(G::FinGenAbGroup, H::FinGenAbGroup, A::Matrix{ <: Map{FinGenAbGroup, FinGenAbGroup}}) -> Map
```

Given groups $G$ and $H$ that are created as direct products as well as a matrix $A$ containing maps $A[i,j] : G_i \to H_j$, return the induced homomorphism.
