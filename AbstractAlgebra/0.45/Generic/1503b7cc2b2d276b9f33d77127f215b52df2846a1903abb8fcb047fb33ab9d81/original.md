```
exponent{T <: RingElem}(a::MPoly{T}, i::Int, j::Int)
```

Return exponent of the j-th variable in the i-th term of the polynomial. Term and variable numbering begins at $1$ and variables are ordered as during the creation of the ring.
