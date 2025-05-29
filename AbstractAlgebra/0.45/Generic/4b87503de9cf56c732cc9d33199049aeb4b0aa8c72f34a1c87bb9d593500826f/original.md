```
setcoeff!(a::MPoly, exps::Vector{Int}, c::S) where S <: RingElement
```

Set the coefficient of the term with the given exponent vector to the given value $c$. This function takes $O(\log n)$ operations if a term with the given exponent already exists, or if the term is inserted at the end of the polynomial. Otherwise it can take $O(n)$ operations in the worst case.
