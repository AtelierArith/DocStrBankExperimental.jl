```
nullspace(M::MatElem{T}) where {T <: FieldElement}
```

Return a tuple $(\nu, N)$ consisting of the nullity $\nu$ of $M$ and a basis $N$ (consisting of column vectors) for the right nullspace of $M$, i.e. such that $MN$ is the zero matrix. If $M$ is an $m\times n$ matrix $N$ will be an $n\times \nu$ matrix.
