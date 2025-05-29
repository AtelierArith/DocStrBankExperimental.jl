```
set_exponent_vector!(a::MPoly{T}, i::Int, exps::Vector{Int}) where T <: RingElement
```

Set the i-th exponent vector to the supplied vector, where the entries correspond to the exponents of the variables in the order supplied when the ring was created. The modified polynomial is returned.
