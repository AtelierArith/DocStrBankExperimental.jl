```
has_complement(i::TorQuadModuleMap) -> Bool, TorQuadModuleMap
```

Given a map representing the injection of a submodule $W$ of a torsion quadratic module $T$, return whether $W$ has a complement $U$ in $T$. If yes, it returns an injection $U \to T$.

Note: if such a $U$ exists, $W$ and $U$ are in direct sum inside $T$ but they are not necessarily orthogonal to each other.
