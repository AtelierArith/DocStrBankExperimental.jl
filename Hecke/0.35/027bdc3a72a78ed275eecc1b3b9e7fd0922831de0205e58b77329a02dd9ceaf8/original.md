```
lift(a::TorQuadModuleElem) -> Vector{QQFieldElem}
```

Lift `a` to the ambient space of `cover(parent(a))`.

For $a + N \in M/N$ this returns the representative $a$.
