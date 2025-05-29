```
HyperellipticCurve(f::PolyRingElem, g::PolyRingElem; check::Bool = true) -> HypellCrv
```

ハイパーエリプティック曲線 $y^2 + h(x)y = f(x)$ を返します。多項式 $f$ は、次数が 2g + 1 > 3 または 2g + 2 > 4 の単項式でなければならず、多項式 h は次数が < g + 2 でなければなりません。ここで g は曲線の属です。
