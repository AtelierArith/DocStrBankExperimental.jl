```
rising_factorial2(x::RingElement, n::Integer)
```

Return a tuple containing the rising factorial $x(x + 1)\cdots (x + n - 1)$ and its derivative. If $n < 0$ we throw a `DomainError()`.

# Examples

```jldoctest
julia> R, x = ZZ[:x];

julia> rising_factorial2(x, 1)
(x, 1)

julia> rising_factorial2(x, 2)
(x^2 + x, 2*x + 1)

julia> rising_factorial2(4, 2)
(20, 9)
```
