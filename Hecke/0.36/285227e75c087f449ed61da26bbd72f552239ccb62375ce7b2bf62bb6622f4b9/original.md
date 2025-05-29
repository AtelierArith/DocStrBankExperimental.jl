```
biproduct(x::Vararg{ZZLat}) -> ZZLat, Vector{AbstractSpaceMor}, Vector{AbstractSpaceMor}
biproduct(x::Vector{ZZLat}) -> ZZLat, Vector{AbstractSpaceMor}, Vector{AbstractSpaceMor}
```

Given a collection of $\mathbb Z$-lattices $L_1, \ldots, L_n$, return their biproduct $L := L_1 \oplus \ldots \oplus L_n$, together with the injections $L_i \to L$ and the projections $L \to L_i$. (seen as maps between the corresponding ambient spaces).

For objects of type `ZZLat`, finite direct sums and finite direct products agree and they are therefore called biproducts. If one wants to obtain `L` as a direct sum with the injections $L_i \to L$, one should call `direct_sum(x)`. If one wants to obtain `L` as a direct product with the projections $L \to L_i$, one should call `direct_product(x)`.
