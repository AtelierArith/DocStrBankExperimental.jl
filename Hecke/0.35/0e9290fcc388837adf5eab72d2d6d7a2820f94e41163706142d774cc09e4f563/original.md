```
direct_product(G::FinGenAbGroup...) -> FinGenAbGroup, Vector{FinGenAbGroupHom}
```

Return the direct product $D$ of the (finitely many) abelian groups $G_i$, together with the projections $D \to G_i$.

For finite abelian groups, finite direct sums and finite direct products agree and they are therefore called biproducts. If one wants to obtain $D$ as a direct sum together with the injections $D \to G_i$, one should call `direct_sum(G...)`. If one wants to obtain $D$ as a biproduct together with the projections and the injections, one should call `biproduct(G...)`.

Otherwise, one could also call `canonical_injections(D)` or `canonical_projections(D)` later on.
