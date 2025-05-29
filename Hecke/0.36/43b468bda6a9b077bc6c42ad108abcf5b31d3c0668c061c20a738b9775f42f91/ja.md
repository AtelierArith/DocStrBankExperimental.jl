```
quo(O::RelNumFieldOrder, I::RelNumFieldOrderIdeal, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
quo(O::AlgAssRelOrd, I::AlgAssRelOrdIdl, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
  -> StructureConstantAlgebra, RelOrdToAlgAssMor
```

理想 $I$ が $p \cdot O \subseteq I \subseteq O$ であるとき、この関数は $O/I$ を有限体 $R/p$ 上の代数として構築します。ここで、$R$ は $p$ の順序であり、射影写像 $O \to O/I$ も含まれます。`R == base_ring(O)` であり、$p$ が素数であると仮定します。
