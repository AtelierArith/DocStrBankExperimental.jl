```
divisor_sigma(x::ZZRingElem, y::Int)
divisor_sigma(x::ZZRingElem, y::ZZRingElem)
divisor_sigma(x::Int, y::Int)
```

シグマ関数の値を返します。すなわち、$\sum_{0 < d \;| x} d^y$です。もし$x \leq 0$または$y < 0$の場合は、`DomainError()`をスローします。

# 例

```jldoctest
julia> divisor_sigma(ZZ(32), 10)
1127000493261825

julia> divisor_sigma(ZZ(32), ZZ(10))
1127000493261825

julia> divisor_sigma(32, 10)
1127000493261825
```
