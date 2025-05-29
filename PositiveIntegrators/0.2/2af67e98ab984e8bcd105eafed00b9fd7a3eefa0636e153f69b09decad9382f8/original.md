```
work_precision_adaptive(prob, algs, labels, abstols, reltols, alg_ref;
                        adaptive_ref = false,
                        abstol_ref = 1e-14,
                        reltol_ref = 1e-13,
                        compute_error = rel_max_error_tend,
                        seconds = 2,
                        numruns = 20,
                        kwargs...)
```

Adds work-precision data to the dictionary `dict`, which was created with `work_precion_fixed_adaptive`. See [`work_precision_adaptive`](@ref) for the meaning of the inputs.
