```
SparsePredCG
```

A `LinPred` type with Conjugate Gradient and a sparse `X`

# Members

  * `X`: Model matrix of size `n` × `p` with `n ≥ p`.  Should be full column rank.
  * `beta0`: base coefficient vector of length `p`
  * `delbeta`: increment to coefficient vector, also of length `p`
  * `scratchbeta`: scratch vector of length `p`, used in [`GLM.linpred!`](@ref) method
