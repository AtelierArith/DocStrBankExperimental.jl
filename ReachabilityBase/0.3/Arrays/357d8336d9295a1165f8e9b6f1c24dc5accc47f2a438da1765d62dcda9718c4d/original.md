```
rectify(x::AbstractArray{N}) where {N<:Real}
```

Rectify an array, i.e., take the element-wise maximum with zero.

### Input

  * `x` – array

### Output

A copy of the array where each negative entry is replaced by zero.
