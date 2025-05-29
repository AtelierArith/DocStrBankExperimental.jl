```
eigenspace(M::MatElem{T}, lambda::T; side::Symbol = :left)
  where T <: FieldElem -> MatElem{T}
```

Return a matrix whose rows (if `side == :left`) or columns (if `side == :right`) give a basis of the eigenspace of $M$ with respect to the eigenvalue $\lambda$. If `side` is `:right`, the right eigenspace is computed, i.e. vectors $v$ such that $Mv = \lambda v$. If `side` is `:left`, the left eigenspace is computed, i.e. vectors $v$ such that $vM = \lambda v$.
