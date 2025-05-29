```
changebasis(P::AbstractFunctionSpace, P′::AbstractFunctionSpace)
```

Return `changebasis_R(P, P′)` if $P ⊆ P′$, otherwise `changebasis_R(P, P′)` if $P ⊑ P′$. Throw an error if $P ⊈ P′$ and $P ⋢ P′$.
