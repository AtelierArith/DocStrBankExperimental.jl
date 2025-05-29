```
crt_with_lcm(r1::T, m1::T, r2::T, m2::T; check::Bool=true) where T <: RingElement
```

Return a tuple consisting of an element congruent to $r_1$ modulo $m_1$ and $r_2$ modulo $m_2$ and the least common multiple of $m_1$ and $m_2$. If `check = true` and no solution exists, an error is thrown.
