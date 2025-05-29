```
falling_factorial(x::RingElement, n::Integer)
```

$$
x
$$

の降下階乗を返します。すなわち、$x(x - 1)(x - 2)\cdots (x - n + 1)$です。もし$n < 0$の場合は、`DomainError()`を投げます。

# 例

```jldoctest
julia> R, x = ZZ[:x];

julia> falling_factorial(x, 1)
x

julia> falling_factorial(x, 2)
x^2 - x

julia> falling_factorial(4, 2)
12
```
