```
divisibility(L::ZZLat, v::Union{Vector, QQMatrix}) -> QQFieldElem
```

Return the divisibility of `v` with respect to `L`.

For a vector `v` in the ambient quadratic space $(V, \Phi)$ of `L`, we call the divisibility of `v` with the respect to `L` the non-negative generator of the fractional $\mathbb Z$-ideal $\Phi(v, L)$.
