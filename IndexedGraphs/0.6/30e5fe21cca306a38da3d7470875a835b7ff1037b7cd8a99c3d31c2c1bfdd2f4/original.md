```
IndexedDiGraph(A::AbstractMatrix)
```

Constructs a IndexedDiGraph from the adjacency matrix A.

`IndexedDiGraph` internally stores the transpose of `A`. To avoid overhead due to the transposition, use `IndexedDiGraph(transpose(At))` where `At` is the  transpose of `A`.
