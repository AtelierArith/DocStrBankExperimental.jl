```
reverse_rows(a::MatrixElem{T}) where T <: NCRingElement
```

Return a matrix $b$ with the entries of $a$, where the $i$th and $r - i$th row is swapped for $1 \leq i \leq r/2$. Here $r$ is the number of rows of $a$.
