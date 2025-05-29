```
    add_column!(F::UpdatableGivensQR, x::AbstractVector, k::Int = size(F, 2) + 1)
```

Given an existing QR factorization `F` of a matrix, computes the factorization of the same matrix after a new column `x` has been added as the `k`ᵗʰ column. Computational complexity: O(nm) where size(F) = (n, m). WARNING: Overwrites existing factorization.
