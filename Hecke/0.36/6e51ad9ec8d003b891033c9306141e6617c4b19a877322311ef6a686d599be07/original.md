```
mod(x::AbsSimpleNumFieldOrderElem, I::AbsNumFieldOrderIdeal)
```

Returns the unique element $y$ of the ambient order of $x$ with $x \equiv y \bmod I$ and the following property: If $a_1,\dotsc,a_d \in \mathbf{Z}_{\geq 1}$ are the diagonal entries of the unique HNF basis matrix of $I$ and $(b_1,\dotsc,b_d)$ is the coefficient vector of $y$, then $0 \leq b_i < a_i$ for $1 \leq i \leq d$.
