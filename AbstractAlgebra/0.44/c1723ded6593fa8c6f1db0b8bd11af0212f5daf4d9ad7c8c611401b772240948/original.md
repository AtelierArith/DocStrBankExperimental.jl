```
extended_weak_popov_with_transform(A::MatElem{T}, V::MatElem{T}) where {T <: PolyRingElem}
```

Compute the weak Popov form $P$ of $A$ by applying simple row transformations on $A$, a vector $W$ by applying the same transformations on the vector $V$, and a transformation matrix $U$ so that $P = UA$. Return the tuple $(P, W, U)$.
