```
reverse_rows!(a::MatrixElem{T}) where T <: NCRingElement
```

Swap the $i$th and $r - i$th row of $a$ for $1 \leq i \leq r/2$, where $r$ is the number of rows of $a$.
