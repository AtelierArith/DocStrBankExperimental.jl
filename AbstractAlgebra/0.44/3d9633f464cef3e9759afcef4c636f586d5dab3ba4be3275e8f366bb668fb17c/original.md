```
comm(g::T, h::T, k::T...) where {T <: GroupElem}
```

Return the left associative iterated commutator $[[g, h], ...]$, where $[g, h] = g^{-1} h^{-1} g h$.
