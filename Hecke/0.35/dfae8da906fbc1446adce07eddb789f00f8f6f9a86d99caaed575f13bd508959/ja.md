```
division_polynomial(E::EllipticCurve, n::Int, x, y) -> Poly
```

楕円曲線 E の n 次除法多項式を、Mazur と Tate に従って、体 k 上で定義されたものとして計算します。x または y が与えられた場合、出力は自動的に与えられた値を使用して評価されます。
