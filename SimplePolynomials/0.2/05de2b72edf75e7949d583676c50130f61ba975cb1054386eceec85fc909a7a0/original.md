```
interpolate(vals::Vector{T})::SimplePolynomial where {T<:Number}
```

Given a list of numbers `vals`, find a polynomial `p` that generates that list. That is, `p(0)` gives the first value on the list, `p(1)` the second value,  and so forth. 
