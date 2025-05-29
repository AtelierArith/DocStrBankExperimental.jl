```
is_zero_divisor(a::T) where T <: RingElement
```

非ゼロの $b$ が存在して $a b = 0$ である場合は `true` を返し、それ以外の場合は `false` を返します。
