```
closure(C::T, G::Vector{T}) where T <: MatElem
```

Given a matrix $C$ representing a subspace of $K^n$ and a list of matrices $G$ representing endomorphisms of $K^n$, the function returns a matrix representing the closure of the subspace under the action, i.e. the smallest subspace of $K^n$ invariant under the endomorphisms.
