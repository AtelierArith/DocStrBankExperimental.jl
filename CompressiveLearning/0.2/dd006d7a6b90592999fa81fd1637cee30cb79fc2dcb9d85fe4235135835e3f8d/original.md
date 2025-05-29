```
WHOrthoRandom(d, m, R; s=3, deterministic=nothing, gaussian_first_block)
```

Creates a fast transforms of the form `Ω = [B₁ᵀ, …, B_rᵀ]` with each `Bᵢ ~iid R[Π_{i=1}^s (HDᵢ)]`, where:

  * `R` is a diagonal matrix with entries provided as argument on the diagonal
  * `H` denotes the Walsh-Hadamard (WH) matrix
  * `Dᵢ` are diagonal matrices with iid Rademacher entries.  When `gaussian_first_block` is set, then the first block `D₁` has Gaussian entries instead of Rademacher.

Orthogonormality holds when the radiuses are set to one.
