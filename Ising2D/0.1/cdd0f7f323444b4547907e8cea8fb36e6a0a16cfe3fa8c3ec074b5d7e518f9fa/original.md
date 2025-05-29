```
mcmc_ising2d!(; s=rand_ising2d(), k=1.0, β=k*β_ising2d, rng=default_rng(),
    algorithm=default_algorithm(), progress=true, 
    nwarmups=1000, nskips=100, niters=5000
)
```

returns the result of the Markov Chain Monte Carlo simulation with length niters, which is the array of the states of 2D Ising model.
