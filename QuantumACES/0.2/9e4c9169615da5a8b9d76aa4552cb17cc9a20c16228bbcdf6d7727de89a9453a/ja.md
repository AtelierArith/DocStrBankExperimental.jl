```
get_full_design(d::Design; diagnostics::Bool = false)
```

デザイン `d` のコピーを返します。このとき、共分散行列の辞書が完全な共分散行列を生成し、`diagnostics` が `true` の場合は診断情報を印刷します。
