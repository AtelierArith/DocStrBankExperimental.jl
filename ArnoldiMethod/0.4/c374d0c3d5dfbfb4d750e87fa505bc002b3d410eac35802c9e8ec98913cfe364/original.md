```
partialeigen(P::PartialSchur) → (Vector{<:Union{Real,Complex}}, Matrix{<:Union{Real,Complex}})
```

Transforms a partial Schur decomposition into an eigendecomposition.

!!! note
    For real-symmetric and complex-Hermitian matrices the Schur vectors coincide with the eigenvectors and the R matrix is diagonal, and hence it is not necessary to call this function in that case.

    In fact, in case of real-symmetric and complex-Hermitian matrices *with repeated eigenvalues*, calling `partialeigen` may be undesirable, as it can return eigenvectors that are not orthogonal. The Schur vectors on the other hand are orthogonal by construction.


The method still relies on LAPACK to compute the eigenvectors of the (quasi) upper triangular matrix `R` from the partial Schur decomposition.

!!! note
    This method is currently type unstable for real matrices, since we have not yet decided how to deal with complex conjugate pairs of eigenvalues. E.g. if almost all eigenvalues are real, but there are just a few conjugate  pairs, should all eigenvectors be complex-valued?

