```
jordan_decomposition(M::MatElem{T}) where T <:FieldElem -> MatElem{T}, MatElem{T}
```

Returns matrices $S$ and $N$ such that $N$ is nilpotent, $S$ is semisimple and $M = S+N$.
