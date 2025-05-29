```
ThermInt([rng::AbstractRNG]; n_steps=30, n_samples=2000, n_warmup=500)
ThermInt([rng::AbstractRNG], schedule; n_samples=2000, n_warmup=500)
```

  * `schedule` can be any iterable object
  * `n_steps` is the number of steps for the schedule using the formula

`(1:n_steps) ./ n_steps).^5`

A `ThermInt` object can then be used as a function:

```julia
    alg = ThermInt(30)
    alg(loglikelihood, logprior, x_init)
```
