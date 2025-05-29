```
weight_kernel!(coeff_terms, log_e_1_terms, log_e_2_terms, φ_old, Ψ, y_t,
    s_t_nontemp, det_HH, inv_HH; initialize = false,
    poolmodel = false)
```

The outputs of the weight_kernel function are meant to speed up the adaptive φ finding, so that we don't do the same matrix multiplication step in every iteration of the root-solving algorithm.

The exponential terms are logged first and then exponentiated in the incremental weight calculation so the problem is well-conditioned (i.e. not exponentiating very large negative numbers).

This function modifies `coeff_terms`, `log_e_1_terms`, and `log_e_2_terms`.
