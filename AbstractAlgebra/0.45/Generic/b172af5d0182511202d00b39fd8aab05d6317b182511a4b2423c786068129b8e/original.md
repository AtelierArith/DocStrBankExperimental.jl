```
gcd(a::RationalFunctionFieldElem{T, U}, b::RationalFunctionFieldElem{T, U}) where {T <: FieldElement, U <: Union{PolyRingElem, MPolyRingElem}}
```

Return a greatest common divisor of $a$ and $b$ if one exists. N.B: we define the GCD of $a/b$ and $c/d$ to be gcd$(ad, bc)/bd$, reduced to lowest terms.
