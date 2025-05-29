```
inv(M::MatrixElem{T}) where {T <: RingElement}
```

Given a non-singular $n\times n$ matrix over a ring, return an $n\times n$ matrix $X$ such that $MX = I_n$, where $I_n$ is the $n\times n$ identity matrix. If $M$ is not invertible over the base ring an exception is raised.
