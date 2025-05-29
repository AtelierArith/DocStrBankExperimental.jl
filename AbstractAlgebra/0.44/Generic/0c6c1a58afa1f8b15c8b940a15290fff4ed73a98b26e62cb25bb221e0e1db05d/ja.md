```
rising_factorial2(x::RingElement, n::Integer)
```

上昇階乗 $x(x + 1)\cdots (x + n - 1)$ とその導関数を含むタプルを返します。もし $n < 0$ の場合は `DomainError()` を投げます。

# 例

```jldoctest
julia> R, x = ZZ[:x];

julia> rising_factorial2(x, 1)
(x, 1)

julia> rising_factorial2(x, 2)
(x^2 + x, 2*x + 1)

julia> rising_factorial2(4, 2)
(20, 9)
```
