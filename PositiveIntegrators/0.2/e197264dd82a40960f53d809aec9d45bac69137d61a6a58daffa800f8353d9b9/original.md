```
work_precision_fixed!(dict, prob, algs, labels, dts, alg_ref;
                      compute_error = rel_max_error_tend,
                      seconds = 2,
                      numruns = 20)
)
```

Adds work-precision data to the dictionary `dict`, which was created with `work_precion_fixed`. See [`work_precision_fixed`](@ref) for the meaning of the inputs.
