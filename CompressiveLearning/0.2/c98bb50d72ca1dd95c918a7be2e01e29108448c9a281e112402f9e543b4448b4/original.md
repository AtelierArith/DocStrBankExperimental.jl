```julia
CLAMP(
    s,
    k,
    skop,
    σX;
    nb_inits,
    tuning,
    tuning_max_its,
    SHyGAMP_max_its,
    sketch_tol,
    uniform_integration_nrep,
    uniform_vars,
    check_finite,
    clip_bad_Qs,
    τ_init,
    debug,
    debug_dic
)

```

“Compressive Learning Approximate Message Passing” algorithm. Recover `k` centroids from the sketch `s`.
