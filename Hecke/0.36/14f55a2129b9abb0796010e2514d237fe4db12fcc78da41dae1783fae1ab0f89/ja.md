```
quo(I::RelNumFieldOrderIdeal, J::RelNumFieldOrderIdeal, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
quo(I::AlgAssRelOrdIdl, J::AlgAssRelOrdIdl, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
  -> StructureConstantAlgebra, RelOrdToAlgAssMor
```

理想 $J$ が $p \cdot I \subseteq J \subseteq I$ を満たすとき、この関数は $I/J$ を有限体 $R/p$ 上の代数として構築します。ここで、$R$ は $p$ の順序であり、射影写像 $I \to I/J$ も含まれます。`order(I) === order(J)` が成り立つと仮定されており、特に両方が定義されている必要があります。さらに、`R == base_ring(order(I))` が成り立ち、$p$ は素数である必要があります。
