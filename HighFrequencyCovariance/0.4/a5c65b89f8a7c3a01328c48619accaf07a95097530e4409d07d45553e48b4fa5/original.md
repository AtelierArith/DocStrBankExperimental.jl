```
project_to_S(
    A::Hermitian,
    W_root::Union{Hermitian,Diagonal};
    W_inv_sqrt::Union{Hermitian,Diagonal} = sqrt_psd(inv(W_root^2)),
)

project_to_S(
    A::Diagonal,
    W_root::Union{Hermitian,Diagonal};
    W_inv_sqrt::Union{Hermitian,Diagonal,Missing} = missing,
)
```

This maps a matrix to the nearest psd matrix. `W_root` should be the principal square root of a psd Hermitian weighting matrix, `W`. `W_inv_sqrt` should be the corresponding square root of the inverse of `W`. `nearest_psd_matrix` is a simpler interface for this function however it does not allow weighting matrices to be specified.

### Inputs

  * `A` - The matrix you want to project to the S space. This can be a `Diagonal` or a `Hermitian`. Note that if you input a `Diagonal` matrix then it is already in the S space and so it will be returned without any calculation.
  * `W_root` - The inverse weighting matrix.
  * `W_inv_sqrt` - The root of `W_root`. This is calculated if you don't have it but it can save some calculation effort if you already have it.

### Outputs

  * A `Hermitian`.

### References

Higham, N. J. 2001. Theorem 3.2
