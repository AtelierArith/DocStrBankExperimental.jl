```
logq(chain::AbstractChain) -> AbstractVector{AbstractFloat}
```

Return a vector of the log-densities of the sampled chain. Should satisfy

```
logq(chain) == getlogdensity(chain).(samples(chain))
```
