```
Base.getindex(M::MatElem, rows, cols)
```

When `rows` and `cols` are specified as an `AbstractVector{Int}`, return a copy of the submatrix $A$ of $M$ defined by `A[i,j] = M[rows[i], cols[j]]` for `i=1,...,length(rows)` and `j=1,...,length(cols)`. Instead of a vector, `rows` and `cols` can also be:

  * an integer `i`, which is  interpreted as `i:i`, or
  * `:`, which is interpreted as `1:nrows(M)` or `1:ncols(M)` respectively.
