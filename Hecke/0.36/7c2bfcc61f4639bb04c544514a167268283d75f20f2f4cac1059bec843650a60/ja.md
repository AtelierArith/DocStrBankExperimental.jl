```
elliptic_curve(f::MPolyRingElem, x::MPolyRingElem, y::MPolyRingElem) -> EllipticCurve
```

長いワイエルシュトラス形式の二変数多項式 `f` から楕円曲線を構築します。第二および第三の引数は、$f = c ⋅ (-y² + x³ - a₁ ⋅ xy + a₂ ⋅ x² - a₃ ⋅ y + a₄ ⋅ x + a₆)$ となるように `f` の親の変数を指定します。
