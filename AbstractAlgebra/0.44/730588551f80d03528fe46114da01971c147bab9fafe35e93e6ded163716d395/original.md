```
add_column(a::MatrixElem{T}, s::RingElement, i::Int, j::Int, rows = 1:nrows(a)) where T <: RingElement
```

Create a copy of $a$ and add $s$ times the $i$-th row to the $j$-th row of $a$.

By default, the transformation is applied to all rows of $a$. This can be changed using the optional `rows` argument.
