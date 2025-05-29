```
quo(I::AbsNumFieldOrderIdeal, J::AbsNumFieldOrderIdeal, p::Union{ Int, ZZRingElem })
quo(I::AlgAssAbsOrdIdl, J::AlgAssAbsOrdIdl, p::Union{ Int, ZZRingElem })
  -> StructureConstantAlgebra, AbsOrdToAlgAssMor
```

理想 $J$ が $p \cdot I \subseteq J \subseteq I$ であるとき、この関数は $I/J$ を $\mathbb F_p$ 上の代数として構築し、射影写像 $I \to I/J$ を提供します。$p$ は素数であると仮定します。
