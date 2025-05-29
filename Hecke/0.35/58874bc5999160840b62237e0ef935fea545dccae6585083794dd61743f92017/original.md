```
hasse_invariant(V::QuadSpace, p::Union{InfPlc, AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> Int
```

Returns the Hasse invariant of the quadratic space `V` at `p`. This is equal to the product of local Hilbert symbols $(a_i, a_j)_p$, $i < j$, where $V$ is isometric to $\langle a_1, \dotsc, a_n\rangle$. If `V` is degenerate return the hasse invariant of `V/radical(V)`.
