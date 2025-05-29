```
lu!(A::BandedMatrix, pivot = Val(true); check = true)
```

Compute the LU factorization of a banded matrix `A` inplace, overwriting the matrix. This factorization requires `A` to have extra storage, and in particular if the banded matrix of interest has bandwidths `(l, u)` then `A` should have bandwidths `(l, l+u)` and contain the desired matrix along with zeros in the additional entries.

When `check = true`, an error is thrown if the factorization fails. When `check = false` it is the user's responsibility for checking the validity of the factorization.
