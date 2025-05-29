```
reverse_cols!(a::MatrixElem{T}) where T <: NCRingElement
```

Swap the $i$th and $r - i$th column of $a$ for $1 \leq i \leq c/2$, where $c$ is the number of columns of $a$.
