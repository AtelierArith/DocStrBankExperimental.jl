```
IndexedBiDiGraph(A::AbstractMatrix)
```

Construct an `IndexedBiDiGraph` from the adjacency matrix `A`. 

`IndexedBiDiGraph` internally stores the transpose of `A`. To avoid overhead due to the transposition, use `IndexedBiDiGraph(transpose(At))` where `At` is the  transpose of `A`.
