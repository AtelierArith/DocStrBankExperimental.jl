```
rand(rng::AbstractRNG, p::Function, s::Walker2014Sampler, x0::Int)
```

Draw the next state in a MCMC with target unnormalized pdf `p` using the sampler `s`, assuming that the current state is `x0`. Both `rng` and `s` are modified in the process.
