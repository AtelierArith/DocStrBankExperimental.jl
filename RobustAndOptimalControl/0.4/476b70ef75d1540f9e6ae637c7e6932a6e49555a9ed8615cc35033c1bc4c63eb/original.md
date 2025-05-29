```
sysm, T, SF = schur_form(sys)
```

Bring `sys` to Schur form.

The Schur form is characterized by `A` being Schur with the real values of eigenvalues of `A` on the main diagonal. `T` is the similarity transform applied to the system such that 

```julia
sysm ≈ similarity_transform(sys, T)
```

`SF` is the Schur-factorization of `A`.

See also [`modal_form`](@ref) and [`hess_form`](@ref)
