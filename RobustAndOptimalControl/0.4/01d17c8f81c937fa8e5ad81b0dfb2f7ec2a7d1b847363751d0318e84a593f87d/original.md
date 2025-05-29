```
sysm, T, HF = hess_form(sys)
```

Bring `sys` to Hessenberg form form.

The Hessenberg form is characterized by `A` having upper Hessenberg structure. `T` is the similarity transform applied to the system such that 

```julia
sysm ≈ similarity_transform(sys, T)
```

`HF` is the Hessenberg-factorization of `A`.

See also [`modal_form`](@ref) and [`schur_form`](@ref)
