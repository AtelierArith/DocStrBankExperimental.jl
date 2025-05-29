```
commutator(g::El, h::El, k::El...) where {El <: GroupElement}
```

Return the left associative iterated commutator $[[g, h], ...]$, where $[g, h] = g^{-1} h^{-1} g h$.
