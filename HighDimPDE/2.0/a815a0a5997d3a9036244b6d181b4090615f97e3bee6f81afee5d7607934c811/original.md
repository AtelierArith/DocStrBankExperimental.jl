```
DeepSplitting(nn, K=1, opt = Flux.Optimise.Adam(0.01), λs = nothing, mc_sample =  NoSampling())
```

Deep splitting algorithm.

# Arguments

  * `nn`: a [Flux.Chain](https://fluxml.ai/Flux.jl/stable/reference/models/layers/#Flux.Chain), or more generally a [functor](https://github.com/FluxML/Functors.jl).
  * `K`: the number of Monte Carlo integrations.
  * `opt`: optimizer to be used. By default, `Flux.Optimise.Adam(0.01)`.
  * `λs`: the learning rates, used sequentially. Defaults to a single value taken from `opt`.
  * `mc_sample::MCSampling` : sampling method for Monte Carlo integrations of the non-local term. Can be `UniformSampling(a,b)`, `NormalSampling(σ_sampling, shifted)`, or `NoSampling` (by default).

# Example

```julia
hls = d + 50 # hidden layer size
d = 10 # size of the sample

# Neural network used by the scheme
nn = Flux.Chain(Dense(d, hls, tanh),
                Dense(hls,hls,tanh),
                Dense(hls, 1, x->x^2))

alg = DeepSplitting(nn, K=10, opt = Flux.Optimise.Adam(), λs = [5e-3,1e-3],
                    mc_sample = UniformSampling(zeros(d), ones(d)) )
```
