```
y = polyval(p::AbstractArray, x::Union{AbstractArray, Number})
```

Evaluates the polynomial p at each point in x. The argument p is a vector of length n+1 whose elements are the coefficients (in ascending order of powers) of an nth-degree polynomial:
