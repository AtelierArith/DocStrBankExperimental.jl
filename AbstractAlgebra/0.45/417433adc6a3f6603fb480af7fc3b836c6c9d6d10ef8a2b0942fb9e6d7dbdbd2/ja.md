```
compose(f::PolyRingElem, g::PolyRingElem; inner)
```

多項式 $a$ を多項式 $b$ と合成し、結果を返します。

  * `inner = :right` の場合、`f(g)` が返されます。
  * `inner = :left` の場合、`g(f)` が返されます。
