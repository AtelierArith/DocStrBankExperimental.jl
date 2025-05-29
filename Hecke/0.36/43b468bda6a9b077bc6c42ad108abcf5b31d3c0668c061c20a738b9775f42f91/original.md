```
quo(O::RelNumFieldOrder, I::RelNumFieldOrderIdeal, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
quo(O::AlgAssRelOrd, I::AlgAssRelOrdIdl, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
  -> StructureConstantAlgebra, RelOrdToAlgAssMor
```

Given an ideal $I$ such that $p \cdot O \subseteq I \subseteq O$ this function constructs $O/I$ as an algebra over the finite field $R/p$, where $R$ is the order of $p$, together with the projection map $O \to O/I$. It is assumed that `R == base_ring(O)` and that $p$ is prime.
