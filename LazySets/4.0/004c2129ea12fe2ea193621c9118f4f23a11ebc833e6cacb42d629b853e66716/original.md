```
same_block_structure(x::AbstractVector{S1}, y::AbstractVector{S2}
                    ) where {S1<:LazySet, S2<:LazySet}
```

Check whether two vectors of sets have the same block structure, i.e., the $i$-th entry in the vectors have the same dimension.

### Input

  * `x` – first vector
  * `y` – second vector

### Output

`true` iff the vectors have the same block structure.
