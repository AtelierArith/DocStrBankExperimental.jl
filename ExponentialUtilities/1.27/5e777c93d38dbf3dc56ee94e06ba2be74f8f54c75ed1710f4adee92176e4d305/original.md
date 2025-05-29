```
expv!(w, t, A, b, Ks, cache)
```

Alternative interface for calculating the action of `exp(t*A)` on the vector `b`, storing the result in `w`. The Krylov iteration is terminated when an error estimate for the matrix exponential in the generated subspace is below the requested tolerance. `Ks` is a `KrylovSubspace` and `typeof(cache)<:HermitianSubspaceCache`, the exact type decides which algorithm is used to compute the subspace exponential.
