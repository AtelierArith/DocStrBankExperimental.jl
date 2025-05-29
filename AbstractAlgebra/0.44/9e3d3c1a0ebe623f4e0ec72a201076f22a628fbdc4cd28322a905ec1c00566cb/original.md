```
add_row!(a::MatrixElem{T}, s::RingElement, i::Int, j::Int, cols = 1:ncols(a)) where T <: RingElement
```

Add $s$ times the $i$-th row to the $j$-th row of $a$.

By default, the transformation is applied to all columns of $a$. This can be changed using the optional `cols` argument.
