```
(e_fwd,theta)=compute_fwd_theta(
    graph::Compgraph{T},
    f;
    coefftype = T,
    tolerance = eps(coefftype) / 2,
    theta_init = big"0.1",
)
```

Return relative forward error and corresponding theta for approximation to `f`.

The first output $e_{fwd}$ is the function that computes the relative forward error$e_{fwd}(z)=|f(z) - p(z)| / |z|$, where $p$ is the polynomial underlying the computational graph `graph`. This is meaningful only if $p$ approximates $f$ in some sense.

The second output $θ$ is the largest positive real number such that $e_{fwd}(θ) ≤ tolerance$, where $tolerance$ is by default the unit roundoff of the data type `coefftype`, which in turn defaults to the type of the coefficients of `graph`.

The value of $θ$ is approximated by using the built-in function `fzero` with starting value set to `theta_init`. By default, this root-finding procedure uses high-precision arithmetic.
