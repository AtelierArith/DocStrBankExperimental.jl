```
is_zero_divisor_with_annihilator(a::T) where T <: RingElement
```

非ゼロの$b$が存在して$a b = 0$である場合は`(true, b)`を返し、そうでない場合は`(false, junk)`を返します。
