```
remove_column!(F::UpdatableGivensQR, k::Int = size(F, 2))
```

Updates the existing QR factorization `F` of a matrix to the factorization of the same matrix after its kᵗʰ column has been deleted. Computational complexity: O(m^2) where size(F) = (n, m).
