```
quo(O::AbsNumFieldOrder, I::AbsNumFieldOrderIdeal, p::Union{ Int, ZZRingElem })
quo(O::AlgAssAbsOrd, I::AlgAssAbsOrdIdl, p::Union{ Int, ZZRingElem })
  -> StructureConstantAlgebra, AbsOrdToAlgAssMor
```

理想 $I$ が $p \cdot O \subseteq I \subseteq O$ であるとき、この関数は $O/I$ を $\mathbb F_p$ 上の代数として構築し、射影写像 $O \to O/I$ を提供します。$p$ は素数であると仮定します。
