```
divides(f::T, g::T) where T <: RingElem
```

ペア `flag, q` を返します。ここで、`flag` は $g$ が $f$ を割り切る場合に `true` に設定され、その場合 `q` は商に設定されます。そうでない場合、`flag` は `false` に設定され、`q` は未定義です。
