```
weak_order(vals::Vector{T}) where {T<:Real}
```

Create a weak order `p` from a list of real numbers. In `p` element `i`  is less than element `j` provided `vals[i] < vals[j]` .
