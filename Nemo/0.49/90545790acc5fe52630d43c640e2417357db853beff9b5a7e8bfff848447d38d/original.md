```
is_power(a::ZZRingElem, n::Int) -> Bool, ZZRingElem
is_power(a::QQFieldElem, n::Int) -> Bool, QQFieldElem
is_power(a::Integer, n::Int) -> Bool, Integer
```

Return `true` and the root if $a$ is an $n$-th power.
