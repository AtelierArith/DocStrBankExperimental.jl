```
sysm, T, E = modal_form(sys; C1 = false)
```

Bring `sys` to modal form.

The modal form is characterized by being tridiagonal with the real values of eigenvalues of `A` on the main diagonal and the complex parts on the first sub and super diagonals. `T` is the similarity transform applied to the system such that 

```julia
sysm ≈ similarity_transform(sys, T)
```

If `C1`, then an additional convention for SISO systems is used, that the `C`-matrix coefficient of real eigenvalues is 1. If `C1 = false`, the `B` and `C` coefficients are chosen in a balanced fashion.

`E` is an eigen factorization of `A`.

The modal form makes apparent which modes are controllable from which inputs, and which are observable from which outputs. Non-minimal realizations may trigger singularity exceptions.

See also [`hess_form`](@ref) and [`schur_form`](@ref)
