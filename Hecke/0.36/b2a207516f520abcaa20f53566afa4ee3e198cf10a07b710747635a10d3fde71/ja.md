```
pr_torsion_basis(E::EllipticCurve{AbsSimpleNumFieldElem}, p::ZZRingElem, r = Int) -> Vector{EllipticCurvePoint}
```

p冪トーション部分群の基底を計算します。rが指定されている場合、アルゴリズムはp^r点を生成する基底を見つけた後に探索を停止します。
