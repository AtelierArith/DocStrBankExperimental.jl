```
stable_faltings_height(E::EllipticCurve{QQFieldElem}, prec::Int) -> Float64
```

Eの安定ファルティングス高を返します。これは、jがj不変量、deltaが判別式、AがEの選択されたモデルの周期格子の共体積であるとき、1/12*(log(denominator(j)) - abs(delta))-1/2log(A)として定義されます。
