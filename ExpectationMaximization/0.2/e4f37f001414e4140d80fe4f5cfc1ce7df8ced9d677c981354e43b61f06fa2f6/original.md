```
Base.@kwdef struct StochasticEM<:AbstractEM
    rng::AbstractRNG = Random.GLOBAL_RNG
end
```

The Stochastic EM algorithm was introduced by G. Celeux, and J. Diebolt. in 1985 in [*The SEM Algorithm: A probabilistic teacher algorithm derived from the EM algorithm for the mixture problem*](https://cir.nii.ac.jp/crid/1574231874553755008).

The default random seed is `Random.GLOBAL_RNG` but it can be changed via `StochasticEM(seed)`.
