```
InducedFlag{T} <: Flag where {T <: Flag}
```

Turns a given Flag into its induced equivalent. E.g. `InducedFlag{Graph}(P2)`, where `P2 = Graph(Bool[0 0 1; 0 0 1; 1 1 0])` is the path on three vertices, describes the Flag corresponding to the induced path density. Only makes sense if there is an equivalent to "edges" in the Flag type `T`.
