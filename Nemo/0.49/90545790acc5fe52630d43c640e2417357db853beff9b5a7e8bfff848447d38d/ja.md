```
is_power(a::ZZRingElem, n::Int) -> Bool, ZZRingElem
is_power(a::QQFieldElem, n::Int) -> Bool, QQFieldElem
is_power(a::Integer, n::Int) -> Bool, Integer
```

$ a $ が $ n $ 階の冪である場合、`true` とその根を返します。
