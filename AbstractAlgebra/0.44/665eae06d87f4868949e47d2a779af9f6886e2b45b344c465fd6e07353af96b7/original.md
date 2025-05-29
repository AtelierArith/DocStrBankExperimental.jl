```
multiply_row!(a::MatrixElem{T}, s::RingElement, i::Int, cols = 1:ncols(a)) where T <: RingElement
```

Multiply the $i$th row of $a$ with $s$.

By default, the transformation is applied to all columns of $a$. This can be changed using the optional `cols` argument.
