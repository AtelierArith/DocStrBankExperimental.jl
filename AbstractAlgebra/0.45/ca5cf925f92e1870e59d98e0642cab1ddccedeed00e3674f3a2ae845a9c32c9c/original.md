```
is_nilpotent(A::MatrixElem{T}) where {T <: RingElement}
```

Return if `A` is nilpotent, i.e. if there exists a natural number $k$ such that $A^k = 0$. If `A` is not square an exception is raised.
