```
minkowski_map(a::NumFieldOrderElem, abs_tol::Int) -> Vector{ArbFieldElem}
```

ミンコフスキー埋め込みの下での $a$ の像を返します。返される配列の各エントリは、半径が `2^-abs_tol` より小さい `ArbFieldElem` 型です。
