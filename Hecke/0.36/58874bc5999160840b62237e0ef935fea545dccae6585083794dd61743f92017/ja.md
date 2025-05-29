```
hasse_invariant(V::QuadSpace, p::Union{InfPlc, AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> Int
```

二次空間 `V` の点 `p` におけるハッセ不変量を返します。これは、$V$ が $\langle a_1, \dotsc, a_n\rangle$ に等長であるとき、$i < j$ の場合の局所ヒルベルト記号 $(a_i, a_j)_p$ の積に等しいです。`V` が退化している場合は、`V/radical(V)` のハッセ不変量を返します。
