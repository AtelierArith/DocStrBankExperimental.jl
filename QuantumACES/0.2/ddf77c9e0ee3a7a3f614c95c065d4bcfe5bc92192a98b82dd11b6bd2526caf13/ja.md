```
get_diag_design(d::Design; diagnostics::Bool = false)
```

デザイン `d` のコピーを返します。ここで、共分散行列辞書は対角共分散行列を生成し、`diagnostics` が `true` の場合は診断情報を印刷します。
