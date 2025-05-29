```julia
abstract type PredrawnShocks
```

# Description

Supplies pre-drawn shocks, which are needed to compute model moments for any guess of the estimated parameters. Assumed to be random, but constant over the estimation procedure (so that the minimization procedure works well). They are however re-simulated when performing bootstrap.
