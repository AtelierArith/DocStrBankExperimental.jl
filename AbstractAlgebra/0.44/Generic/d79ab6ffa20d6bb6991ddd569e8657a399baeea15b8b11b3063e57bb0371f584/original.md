```
exponent_word(a::FreeAssociativeAlgebraElem{T}, i::Int) where T <: RingElement
```

Return a vector of variable indices corresponding to the monomial of the $i$-th term of $a$. Term numbering begins at $1$, and the variable indices are given in the order of the variables for the ring.
