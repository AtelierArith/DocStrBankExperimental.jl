```
gcdx(a::OrdLocElem{T}, b::OrdLocElem{T}) where {T <: AbsSimpleNumFieldElem}
```

Returns tuple `(g,u,v)` s.th. `g` = gcd($a$,$b$) and `g` = `u` * $a$ + `v` * $b$.
