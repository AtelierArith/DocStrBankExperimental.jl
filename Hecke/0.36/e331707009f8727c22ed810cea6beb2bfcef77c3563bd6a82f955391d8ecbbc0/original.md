```
getindex(x::FinGenAbGroupElem, v::AbstractVector{Int}) -> Vector{ZZRingElem}
```

Returns the $i$-th components of the element $x$ where $i \in v$.

!!! note
    This function is inefficient since the elements are internally stored using ZZMatrix but this function outputs a vector.

