```
(e_bwd,theta)=compute_bwd_theta(;
    bnd_rel_err = compute_bnd_rel_bwd_err(:exp, graph),
    tolerance = eps(coefftype) / 2,
    theta_init = big"0.2",
    use_log = false,
)

(e_bwd,theta)=compute_bwd_theta(
    graph::Compgraph{T};
    coefftype = T,
    numterms = 100,
    numdigits = 100,
    tolerance = eps(coefftype) / 2,
    theta_init = big"0.2",
    use_log = false,
)
```

Compute bound on relative backward error with corresponding theta.

The first output $e_{bwd}$ is a function that returns a bound on the relative backward error of the polynomial underlying the computational graph `graph`, seen as an approximant to the exponential. For the underlying polynomial $p$, the function returns a bound on `|δ|` where `δ` is such that exp(z+δ) = p(z). This function is computed using `compute_bnd_rel_bwd_err(:graph)`.

The second output $θ$ is the largest positive real number such that $e_{bwd}(θ) ≤ tolerance$, where $tolerance$ is by default the unit roundoff of the data type `coefftype`, which in turn defaults to the type of the coefficients of `graph`.

The value of $theta$ is estimated by approximately solving the equation $e_{bwd}(z) = tolerance$, using the built-in function `fzero` with starting value set to `theta_init`. By default this root-finding procedure uses high-precision arithmetic.

If the kwarg `use_log` is set to `true`, then the value of $theta$ is computed by approximating a solution to the equation $log(e_{bwd}(z)) = log(tolerance)$ instead.

The alternative form accepts a function that returns a bound on the relative backward error. By default, the function is constructed with `compute_bnd_rel_bwd_err(:exp, ...)` and the default values for the kwargs in the first form.
