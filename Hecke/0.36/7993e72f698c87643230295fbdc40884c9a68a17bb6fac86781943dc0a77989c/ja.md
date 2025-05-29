```
torsion_structure(E::EllipticCurve{QQFieldElem}) -> (A::Vector{ZZRingElem},
                                       B::Vector{EllipticCurvePoint{QQFieldElem}}
```

楕円曲線 $E$ の有理トーション群の構造を計算します。すると、`A` は `A = [n]` または `A = [n,m]` の形の配列であり、$E$ の有理トーションは $\mathbf Z/n\mathbf Z$ または $\mathbf Z/n\mathbf Z \times \mathbf Z/m\mathbf Z$ に同型です。また、`B` は点の配列であり、`B = [P]` の場合、$P$ の位数は $n$ であり、または `B = [P, Q]` の場合、$P$ の位数は $n$ であり、$Q$ の位数は $m$ です。
