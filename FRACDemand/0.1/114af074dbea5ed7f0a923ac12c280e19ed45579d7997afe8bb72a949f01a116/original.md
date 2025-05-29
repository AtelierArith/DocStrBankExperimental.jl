```
price_elasticities!(problem::FRACProblem;
    monte_carlo_draws::Int=50,
    draw_method::Symbol=:normal,
    antithetic::Bool=false,
    common_draws::Bool=false,
    halton_skip::Int=500)
```

Compute and store the full matrix of own- and cross-price elasticities for each market. Additional keyword arguments control the Monte Carlo draws:   • draw*method=:normal or :halton   • antithetic=true to use antithetic normals (only for :normal)   • common*draws=true to use the same draws across all markets   • halton_skip sets the skip (burn-in) for Halton sequences
