```
gcd(a::T, b::T) where T <: RingElem
```

Return a greatest common divisor of $a$ and $b$, i.e., an element $g$ which is a common divisor of $a$ and $b$, and with the property that any other common divisor of $a$ and $b$ divides $g$.

!!! note
    For best compatibility with the internal assumptions made by AbstractAlgebra, the return is expected to be unit-normalized in such a way that if the return is a unit, that unit should be one.

