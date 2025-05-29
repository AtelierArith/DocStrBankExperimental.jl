```
Amodule(A::AbstractAssociativeAlgebra, M::Vector{<:MatElem})
```

Given an algebra $A$ over a field $K$ and a list of $\dim(A)$ of square matrices over $K$, construct the $A$-module with `basis(A)[i]` acting via `M[i]` from the right.
