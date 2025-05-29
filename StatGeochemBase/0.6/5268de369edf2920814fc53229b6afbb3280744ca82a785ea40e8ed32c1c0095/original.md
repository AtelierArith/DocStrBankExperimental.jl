```julia
normproduct_ll(μ1, σ1, μ2, σ2)
```

Fast log likelihood proportional to the integral of N[μ1,σ1] * N[μ2,σ2] As `normlogproduct`, but using the fast log likelihood of a Normal distribution (i.e., without the preexponential terms).
