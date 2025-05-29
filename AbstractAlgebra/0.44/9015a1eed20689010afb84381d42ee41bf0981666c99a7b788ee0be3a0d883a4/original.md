```
multiply_column(a::MatrixElem{T}, s::RingElement, i::Int, rows = 1:nrows(a)) where T <: RingElement
```

Create a copy of $a$ and multiply the $i$th column of $a$ with $s$.

By default, the transformation is applied to all rows of $a$. This can be changed using the optional `rows` argument.
