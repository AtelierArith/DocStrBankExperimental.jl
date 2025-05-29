```
short_weierstrass_model(E::EllipticCurve{QQFieldElem}) ->
  (EE::EllipticCurve, EllCrvIso, EllCrvIso)
```

QQ上のロング・ワイエルストラス形式で与えられた曲線をショート・ワイエルストラス形式に変換します。ショート形式と曲線上の点の両方の変換を返します。最初の変換はE（ロング形式）からEE（ショート形式）へのもので、2番目の変換はこの写像の逆です。
