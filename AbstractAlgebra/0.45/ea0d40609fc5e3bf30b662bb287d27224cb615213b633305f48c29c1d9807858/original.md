```
pseudo_inv(M::MatrixElem{T}) where {T <: RingElement}
```

Given a non-singular $n\times n$ matrix $M$ over a ring return a tuple $X, d$ consisting of an $n\times n$ matrix $X$ and a denominator $d$ such that $MX = dI_n$, where $I_n$ is the $n\times n$ identity matrix. The denominator will be the determinant of $M$ up to sign. If $M$ is singular an exception is raised.
