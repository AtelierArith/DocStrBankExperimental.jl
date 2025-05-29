```
unit_group(O::AbsSimpleNumFieldOrder) -> FinGenAbGroup, Map
```

Returns a group $U$ and an isomorphism map $f \colon U \to \mathcal O^\times$. A set of fundamental units of $\mathcal O$ can be obtained via `[ f(U[1+i]) for i in 1:unit_group_rank(O) ]`. `f(U[1])` will give a generator for the torsion subgroup.
