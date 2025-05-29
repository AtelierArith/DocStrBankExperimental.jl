```
is_zero_divisor_with_annihilator(a::T) where T <: RingElement
```

Return `(true, b)` if there exists a nonzero $b$ such that $a b = 0$ and `(false, junk)` otherwise.
