```
gcd(a::FracElem{T}, b::FracElem{T}) where {T <: RingElem}
```

Return a greatest common divisor of $a$ and $b$ if one exists. N.B: we define the GCD of $a/b$ and $c/d$ to be gcd$(ad, bc)/bd$, reduced to lowest terms. This requires the existence of a greatest common divisor function for the base ring.
