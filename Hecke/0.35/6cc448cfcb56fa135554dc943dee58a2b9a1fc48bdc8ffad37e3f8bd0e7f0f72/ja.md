```
short_weierstrass_model(E::EllipticCurve{QQFieldElem}) ->
  (EE::EllipticCurve, EllCrvIso, EllCrvIso)
```

QQ上のロング・ワイエルシュトラス形式で与えられた曲線をショート・ワイエルシュトラス形式に変換します。ショート形式と、曲線上の点に対する両方の変換を返します。最初の変換はE（ロング形式）からEE（ショート形式）へのもので、2番目の変換はこの写像の逆です。
