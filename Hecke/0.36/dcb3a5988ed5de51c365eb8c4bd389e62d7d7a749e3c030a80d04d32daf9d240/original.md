```
quo(I::AbsNumFieldOrderIdeal, J::AbsNumFieldOrderIdeal, p::Union{ Int, ZZRingElem })
quo(I::AlgAssAbsOrdIdl, J::AlgAssAbsOrdIdl, p::Union{ Int, ZZRingElem })
  -> StructureConstantAlgebra, AbsOrdToAlgAssMor
```

Given an ideal $J$ such that $p \cdot I \subseteq J \subseteq I$ this function constructs $I/J$ as an algebra over $\mathbb F_p$ together with the projection map $I \to I/J$. It is assumed that $p$ is prime.
