```
Gibbs(algs...)
```

Compositional MCMC interface. Gibbs sampling combines one or more sampling algorithms, each of which samples from a different set of variables in a model.

Example:

```julia
@model function gibbs_example(x)
    v1 ~ Normal(0,1)
    v2 ~ Categorical(5)
end

# Use PG for a 'v2' variable, and use HMC for the 'v1' variable.
# Note that v2 is discrete, so the PG sampler is more appropriate
# than is HMC.
alg = Gibbs(HMC(0.2, 3, :v1), PG(20, :v2))
```

One can also pass the number of iterations for each Gibbs component using the following syntax:

  * `alg = Gibbs((HMC(0.2, 3, :v1), n_hmc), (PG(20, :v2), n_pg))`

where `n_hmc` and `n_pg` are the number of HMC and PG iterations for each Gibbs iteration.

Tips:

  * `HMC` and `NUTS` are fast samplers and can throw off particle-based

methods like Particle Gibbs. You can increase the effectiveness of particle sampling by including more particles in the particle sampler.
