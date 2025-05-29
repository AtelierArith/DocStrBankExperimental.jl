```
is_zero_divisor(a::T) where T <: RingElement
```

非ゼロの $b$ が存在して $a b = 0$ であれば `true` を返し、そうでなければ `false` を返します。
