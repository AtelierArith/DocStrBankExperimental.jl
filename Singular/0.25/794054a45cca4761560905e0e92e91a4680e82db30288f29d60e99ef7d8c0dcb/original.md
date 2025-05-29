```
reduce(p::S, G::sideal{S}) where S <: SPolyUnion
```

Return the polynomial which is $p$ reduced by the polynomials generating $G$. The ideal $G$ need not be a Groebner basis. For PLURAL rings (S <: spluralg, GAlgebra, WeylAlgebra), the reduction is only a left reduction, and hence cannot be used to test membership in a two-sided ideal. For LETTERPLACE rings (S <: slpalg, FreeAlgebra), the reduction is the full two-sided reduction as only two-sided ideals can be constructed here.
