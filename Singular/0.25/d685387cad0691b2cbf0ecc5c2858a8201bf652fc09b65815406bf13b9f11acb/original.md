```
reduce(I::sideal{S}, G::sideal{S}) where S <: SPolyUnion
```

Return an ideal whose generators are the generators of $I$ reduced by the ideal $G$. The ideal $G$ need not be a Groebner basis. The returned ideal will have the same number of generators as $I$, even if they are zero. For PLURAL rings (S <: spluralg, GAlgebra, WeylAlgebra), the reduction is only a left reduction, and hence cannot be used to test containment in a two-sided ideal. For LETTERPLACE rings (S <: slpalg, FreeAlgebra), the reduction is two-sided as only two-sided ideals can be constructed here.
