```
state_supersinglet([T=ComplexF64,] N::Integer = 3; v::Real = 1)
```

Produces the `N`-partite `N`-level singlet state with visibility `v`. This state is invariant under simultaneous rotations on all parties: $(U ⊗ ... ⊗ U) ρ (U ⊗ ... ⊗ U)' = ρ$.

Reference: Adán Cabello, [arXiv:quant-ph/0203119](https://arxiv.org/abs/quant-ph/0203119)
