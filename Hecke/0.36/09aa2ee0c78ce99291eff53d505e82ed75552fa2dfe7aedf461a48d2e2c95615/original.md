```
quo(O::AbsNumFieldOrder, I::AbsNumFieldOrderIdeal, p::Union{ Int, ZZRingElem })
quo(O::AlgAssAbsOrd, I::AlgAssAbsOrdIdl, p::Union{ Int, ZZRingElem })
  -> StructureConstantAlgebra, AbsOrdToAlgAssMor
```

Given an ideal $I$ such that $p \cdot O \subseteq I \subseteq O$ this function constructs $O/I$ as an algebra over $\mathbb F_p$ together with the projection map $O \to O/I$. It is assumed that $p$ is prime.
