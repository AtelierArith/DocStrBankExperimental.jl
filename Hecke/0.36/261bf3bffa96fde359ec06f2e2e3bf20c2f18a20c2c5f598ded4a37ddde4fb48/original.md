```
direct_sum(G::FinGenAbGroup...) -> FinGenAbGroup, Vector{FinGenAbGroupHom}
```

Return the direct sum $D$ of the (finitely many) abelian groups $G_i$, together with the injections $G_i \to D$.

For finite abelian groups, finite direct sums and finite direct products agree and they are therefore called biproducts. If one wants to obtain $D$ as a direct product together with the projections $D \to G_i$, one should call `direct_product(G...)`. If one wants to obtain $D$ as a biproduct together with the projections and the injections, one should call `biproduct(G...)`.

Otherwise, one could also call `canonical_injections(D)` or `canonical_projections(D)` later on.
