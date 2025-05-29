```
inpolygon!(INSIDE::Matrix, PolyX::Vector, PolyY::Vector, X::Matrix, Y::Matrix; fast=false)
```

行列 `X` と `Y` で与えられた点が、`PolyX` と `PolyY` で与えられた多角形の内側または上にあるか（両方のケースで true を返す）をチェックします。ブール値 `fast` は、多角形のエッジ上に正確にある点を見逃す可能性があるより高速なバージョンをトリガーします。速度向上は 3 倍です。
