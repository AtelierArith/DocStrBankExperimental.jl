```
local_height(P::EllipticCurvePoint{QQFieldElem}, p::IntegerUnion, prec::Int) -> ArbField
```

点 $P$ の局所高さを計算します。これは、$\mathbf{Q}$ 上で定義された楕円曲線の上にあります。数 $p$ は素数または $0$ でなければなりません。後者の場合、無限大の位置での高さが返されます。
