```
rising_factorial(x::RingElement, n::Integer)
```

Return the rising factorial of $x$, i.e. $x(x + 1)(x + 2)\cdots (x + n - 1)$. If $n < 0$ we throw a `DomainError()`.

# Examples

```jldoctest
julia> R, x = ZZ[:x];

julia> rising_factorial(x, 1)
x

julia> rising_factorial(x, 2)
x^2 + x

julia> rising_factorial(4, 2)
20
```
