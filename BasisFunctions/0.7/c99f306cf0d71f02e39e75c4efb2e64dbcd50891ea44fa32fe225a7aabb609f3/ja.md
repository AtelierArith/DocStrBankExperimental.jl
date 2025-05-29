```
conversion([::Type{T}, ]src::Dictionary, dest::Dictionary; options...)
```

ソース辞書から宛先辞書の係数に変換する演算子を構築します。

変換は、有限精度計算の副作用を除いて正確です。
