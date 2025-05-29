```
Noisemodel(logpdf::Function, 
sigma_start::Float64, 
sigma_range::Tuple{Float64,Float64}, 
proposal::Distribution)
```

Return a Noisemodel object with `logpdf` Function to calculate log likelihood of measurements (set this between `logp_gauss` and `logp_rician`),  `sigma_start` as the starting value of noise level, `sigma_range` as prior range and `proposal` distribution for MCMC sampling.

# Examples

```julia-repl
julia> Noisemodel()
Noisemodel(Microstructure.logp_gauss, 0.01, (0.005, 0.1), Distributions.Normal{Float64}(μ=0.0, σ=0.005))
```

```julia-repl
julia> Noisemodel(logpdf = logp_rician, sigma_start = 0.02, proposal = Normal(0,0.001))
Noisemodel(Microstructure.logp_rician, 0.02, (0.005, 0.1), Normal{Float64}(μ=0.0, σ=0.001))
```
