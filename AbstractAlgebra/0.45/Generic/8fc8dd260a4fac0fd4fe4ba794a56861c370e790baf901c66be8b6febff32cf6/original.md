```
divrem(a::MPoly{T}, b::Vector{MPoly{T}}) where {T <: RingElement}
```

Return a tuple `(q, r)` consisting of an array of polynomials `q`, one for each polynomial in `b`, and a polynomial `r` such that `a = sum_i b[i]*q[i] + r`.
