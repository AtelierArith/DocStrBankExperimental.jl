```
quo(I::RelNumFieldOrderIdeal, J::RelNumFieldOrderIdeal, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
quo(I::AlgAssRelOrdIdl, J::AlgAssRelOrdIdl, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
  -> StructureConstantAlgebra, RelOrdToAlgAssMor
```

Given an ideal $J$ such that $p \cdot I \subseteq J \subseteq I$ this function constructs $I/J$ as an algebra over the finite field $R/p$, where $R$ is the order of $p$, together with the projection map $I \to I/J$. It is assumed that `order(I) === order(J)` and in particular both should be defined. Further, it should hold `R == base_ring(order(I))` and $p$ should be prime.
