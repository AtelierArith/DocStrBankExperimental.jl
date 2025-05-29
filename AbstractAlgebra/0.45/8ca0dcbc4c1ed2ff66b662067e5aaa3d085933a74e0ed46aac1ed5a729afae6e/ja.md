```
powermod(f::T, e::Int, m::T) where T <: RingElem
```

`mod(f^e, m)`を返しますが、より効率的に計算される可能性があります。
