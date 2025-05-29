```
vector_fitting(
    s,
    f,
    init_poles,
    weight = 1;
    relaxed = true,
    force_stable = true,
    maxiter = 5,
    tol = 1e-12,
) -> poles, residues, d, h, fitted, error_norm
```

Vector Fitting of the array `f` with complex frequency `s` using a set of initial poles `init_poles`.

`f` can be a matrix of dimensions `(Ns, Nc)` and the fitting will be over its columns using a set of common poles.

`relaxed` controls the nontriviality constraint. `relaxed=true` usually converges faster, but can be less stable for non-smooth functions.

`force_stable` controls if unstable poles should be reflected to the semi-left complex plane, that is, forced to have negative real part.

`maxiter` is the maximum of iterations that will be done to try to achieve a convergence with desired `error_norm` tolerance `tol`.

See also [`recommended_init_poles`](@ref), [`rational`](@ref), [`pole_identification`](@ref), [`residue_identification`](@ref).
