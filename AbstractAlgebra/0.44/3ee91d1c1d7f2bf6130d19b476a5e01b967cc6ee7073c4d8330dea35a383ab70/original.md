```
extended_weak_popov(A::MatElem{T}, V::MatElem{T}) where {T <: PolyRingElem}
```

Compute the weak Popov form $P$ of $A$ by applying simple row transformations on $A$ and a vector $W$ by applying the same transformations on the vector $V$. Return the tuple $(P, W)$.
