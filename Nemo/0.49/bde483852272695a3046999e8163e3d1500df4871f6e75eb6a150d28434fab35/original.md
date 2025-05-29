```
reconstruct(a::ZZRingElem, m::ZZRingElem)
reconstruct(a::ZZRingElem, m::Integer)
reconstruct(a::Integer, m::ZZRingElem)
reconstruct(a::Integer, m::Integer)
```

Attempt to return a rational number $n/d$ such that $0 \leq |n| \leq \lfloor\sqrt{m/2}\rfloor$ and $0 < d \leq \lfloor\sqrt{m/2}\rfloor$ such that gcd$(n, d) = 1$ and $a \equiv nd^{-1} \pmod{m}$. If no solution exists, an exception is thrown.

# Examples

```jldoctest
julia> a = reconstruct(7, 13)
1//2

julia> b = reconstruct(ZZ(15), 31)
-1//2

julia> c = reconstruct(ZZ(123), ZZ(237))
9//2
```
