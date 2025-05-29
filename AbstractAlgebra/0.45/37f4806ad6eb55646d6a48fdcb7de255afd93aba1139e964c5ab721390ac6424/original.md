```
deflation(f::MPolyRingElem{T}) where T <: RingElement
```

Compute deflation parameters for the exponents of the polynomial $f$. This is a pair of arrays of integers, the first array of which (the shift) gives the minimum exponent for each variable of the polynomial, and the second of which (the deflation) gives the gcds of all the exponents after subtracting the shift, again per variable. This functionality is used by gcd (and can be used by factorisation algorithms).
