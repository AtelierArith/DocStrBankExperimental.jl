```
exponent_vector(a::MPoly{T}, i::Int) where T <: RingElement
```

Return a vector of exponents, corresponding to the exponent vector of the i-th term of the polynomial. Term numbering begins at $1$ and the exponents are given in the order of the variables for the ring, as supplied when the ring was created.
