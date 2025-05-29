```
lcgfp = lefschetz_gfp_conversion(lc::LefschetzComplex, p::Int)
```

レフシェッツ複体を有限体上の同じ複体に変換します。

与えられたレフシェッツ複体 `lc` の境界行列は有理数上で定義されていることが期待され、ターゲットの特性 `p` は素数である必要があります。
