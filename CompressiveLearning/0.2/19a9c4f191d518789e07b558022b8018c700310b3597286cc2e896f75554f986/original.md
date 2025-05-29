```
Fastfood(d, m, radiuses)
```

Creates a Fastfood transforms of the form `Ω = [B₁ᵀ, …, B_rᵀ]` with each `Bᵢ ~iid RHGΠHD`, where:

  * `R` is a diagonal matrix chosen such that the l₂-norms of the rows of the blocks are the one provided in `radiuses`;
  * `H` is the Walsh-Hadamard (WH) matrix;
  * `D` is a diagonal matrices with iid Rademacher entries on the diagonal.

Orthogonormality holds when the radiuses are set to one.
