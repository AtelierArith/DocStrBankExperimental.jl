```
hnf_kb_with_transform(A::MatrixElem{T}) where {T <: RingElement}
```

Compute the upper right row Hermite normal form $H$ of $A$ and an invertible matrix $U$ with $UA = H$ using a modification of the algorithm of Kannan-Bachem.
