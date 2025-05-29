```
gcd(a::ResElem{T}, b::ResElem{T}) where {T <: RingElement}
```

Return a greatest common divisor of $a$ and $b$ if one exists. This is done by taking the greatest common divisor of the data associated with the supplied residues and taking its greatest common divisor with the modulus.
