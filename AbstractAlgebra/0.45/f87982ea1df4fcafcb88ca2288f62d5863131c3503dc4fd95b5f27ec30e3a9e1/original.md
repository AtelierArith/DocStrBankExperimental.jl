```
hnf_minors(A::MatrixElem{T}) where {T <: RingElement}
```

Compute the upper right row Hermite normal form of $A$ using the algorithm of Kannan-Bachem. The input must have full column rank.
