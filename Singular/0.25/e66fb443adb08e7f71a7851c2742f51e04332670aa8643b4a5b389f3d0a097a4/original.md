```
reduce(M::smodule, G::smodule; complete_reduction::Bool = true)
```

Return a submodule whose generators are the generators of $M$ reduced by the submodule $G$. The submodule $G$ need not be a Groebner basis. The returned submodule will have the same number of generators as $M$, even if they are zero.
