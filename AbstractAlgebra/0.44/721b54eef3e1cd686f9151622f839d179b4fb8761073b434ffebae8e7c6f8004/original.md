```
hessenberg(A::MatrixElem{T}) where {T <: RingElement}
```

Return the Hessenberg form of $M$, i.e. an upper Hessenberg matrix which is similar to $M$. The upper Hessenberg form has nonzero entries above and on the diagonal and in the diagonal line immediately below the diagonal.
