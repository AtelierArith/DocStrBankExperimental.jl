```
gcdx(a::OrdLocElem{T}, b::OrdLocElem{T}) where {T <: AbsSimpleNumFieldElem}
```

タプル `(g,u,v)` を返します。ここで `g` = gcd($a$,$b$) であり、`g` = `u` * $a$ + `v` * $b$ です。
