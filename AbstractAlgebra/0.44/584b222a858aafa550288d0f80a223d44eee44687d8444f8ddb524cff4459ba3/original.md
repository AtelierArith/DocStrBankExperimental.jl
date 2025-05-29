```
reverse_cols(a::MatrixElem{T}) where T <: NCRingElement
```

Return a matrix $b$ with the entries of $a$, where the $i$th and $r - i$th column is swapped for $1 \leq i \leq c/2$. Here $c$ is the number of columns of$a$.
