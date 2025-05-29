```
crt(r1::T, m1::T, r2::T, m2::T; check::Bool=true) where T <: RingElement
```

Return an element congruent to $r_1$ modulo $m_1$ and $r_2$ modulo $m_2$. If `check = true` and no solution exists, an error is thrown.

If `T` is a fixed precision integer type (like `Int`), the result will be correct if `abs(ri) <= abs(mi)` and `abs(m1 * m2) < typemax(T)`.
