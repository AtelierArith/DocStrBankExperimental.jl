```
biproduct(G::FinGenAbGroup...) -> FinGenAbGroup, Vector{FinGenAbGroupHom}, Vector{FinGenAbGroupHom}
```

Return the direct product $D$ of the (finitely many) abelian groups $G_i$, together with the projections $D \to G_i$ and the injections $G_i \to D$.

For finite abelian groups, finite direct sums and finite direct products agree and they are therefore called biproducts. If one wants to obtain $D$ as a direct sum together with the injections $G_i \to D$, one should call `direct_sum(G...)`. If one wants to obtain $D$ as a direct product together with the projections $D \to G_i$, one should call `direct_product(G...)`.

Otherwise, one could also call `canonical_injections(D)` or `canonical_projections(D)` later on.
