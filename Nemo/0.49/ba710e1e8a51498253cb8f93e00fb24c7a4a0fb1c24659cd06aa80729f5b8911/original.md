```
divisor_sigma(x::ZZRingElem, y::Int)
divisor_sigma(x::ZZRingElem, y::ZZRingElem)
divisor_sigma(x::Int, y::Int)
```

Return the value of the sigma function, i.e. $\sum_{0 < d \;| x} d^y$. If $x \leq 0$ or $y < 0$ we throw a `DomainError()`.

# Examples

```jldoctest
julia> divisor_sigma(ZZ(32), 10)
1127000493261825

julia> divisor_sigma(ZZ(32), ZZ(10))
1127000493261825

julia> divisor_sigma(32, 10)
1127000493261825
```
