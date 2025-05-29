```
FaceContinuous(b::Int, n::Int)
FaceContinuous(::Type{T}, b::Int, n::Int)
```

For `n` dimensions, use `b` bits of precision in this Hilbert curve. If you specify a type `T`, this will be used as the type of the Hilbert encoding. If not, the smallest unsigned integer that can hold `n*b` bits will be used for the Hilbert index data type.

This is the Butz algorithm, as presented by Lawder. Haverkort2017 says it is face continuous. The code is in lawder.c. The original paper had an error, and Lawder put a correction on his website. http://www.dcs.bbk.ac.uk/~jkl/publications.html
