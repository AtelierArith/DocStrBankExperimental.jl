```
sample(model, AIS(N), Ns[; optional args])
sample(model, AIS(N), MCMCThreads(), Ns, Nc[; optional keyword args])
sample(model, AIS(N), MCMCDistributed(), Ns, Nc[; optional keyword args])
```

# Generalities

This function will run an Affine Invariant MCMC sampler, and will return a `Particles` object for each parameter, the mandatory parameters are:

`model`: a subtype of `AbstractDensity`, look at `ApproxPosterior`, `ApproxKernelizedPosterior`, `CommonLogDensity`.

`N`: number of particles in the ensemble, this particles will be evolved to generate new samples.

`Ns`: total number of samples which must be recorded.

`Nc`: total number of chains to run in parallel if MCMCThreads or MCMCDistributed is enabled.

the optional arguments available are:

`discard_initial`: number of mcmc particles to discard before saving any sample.

`ntransitions`: number of mcmc steps per particle between each sample.

`retry_sampling`: number of maximum attempts to resample an initial particle whose cost (or log-density) is ±∞ or NaN.

`progress`: a boolean to disable verbosity

# Minimal Example for `CommonLogDensity`:

```julia
using KissABC
D = CommonLogDensity(
    2, #number of parameters
    rng -> randn(rng, 2), # initial sampling strategy
    x -> -100 * (x[1] - x[2]^2)^2 - (x[2] - 1)^2, # rosenbrock banana log-density
)
res = sample(D, AIS(50), 1000, ntransitions = 100, discard_initial = 500, progress = false)
println(res)
```

output:

```
Particles{Float64,1000}[1.43 ± 1.4, 0.99 ± 0.67]
```

# Minimal Example for `ApproxKernelizedPosterior` (`ApproxPosterior`)

```julia
using KissABC
prior = Uniform(-10, 10) # prior distribution for parameter
sim(μ) = μ + rand((randn() * 0.1, randn())) # simulator function
cost(x) = abs(sim(x) - 0.0) # cost function to compare simulations to target data, in this case simply '0'
plan = ApproxPosterior(prior, cost, 0.01) # Approximate model of log-posterior density (ABC)
#                                           ApproxKernelizedPosterior can be used in the same fashion
res = sample(plan, AIS(100), 2000, discard_initial = 10000, progress = false)
println(res)
```

output:

```
0.0 ± 0.46
```
