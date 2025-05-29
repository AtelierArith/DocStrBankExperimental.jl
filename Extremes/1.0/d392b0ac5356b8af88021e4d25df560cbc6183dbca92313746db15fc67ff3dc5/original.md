```
gumbelfitbayes(model::BlockMaxima{Gumbel};
    niter::Int=5000,
    warmup::Int=2000)
```

Generate a sample from the `BlockMaxima` model parameters' posterior distribution.
