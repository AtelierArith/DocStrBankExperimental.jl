```
differentiate(a::TaylorN{T}, ntup::NTuple{N,Int})
```

Return a `TaylorN` with the partial derivative of `a` defined by `ntup::NTuple{N,Int}`, where the first entry is the number of derivatives with respect to the first variable, the second is the number of derivatives with respect to the second, and so on.
