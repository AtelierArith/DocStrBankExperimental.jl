```
metropolis(ll::Function(θ), R::Int, θ₀::Vector, draw::Function(θ) = naive_sampler(θ₀))
```

Performs MCMC sampling using the marginal Metropolis (-Hastings) algorithm `draw = θ -> θ'` samples a new parameter vector given an old parameter vector. The distribution must be symmetric, e.g., a Gaussian. `R` is the number of iterations. See `log_likelihood_fun`

# Example:

```julia
filter_from_parameters(θ) = ParticleFilter(N, dynamics, measurement, MvNormal(n,exp(θ[1])), MvNormal(p,exp(θ[2])), d0)
priors = [Normal(0,0.1),Normal(0,0.1)]
ll     = log_likelihood_fun(filter_from_parameters,priors,u,y,1)
θ₀ = log.([1.,1.]) # Initial point
draw = θ -> θ .+ rand(MvNormal(0.1ones(2))) # Function that proposes new parameters (has to be symmetric)
burnin = 200 # If using threaded call, provide number of burnin iterations
# @time theta, lls = metropolis(ll, 2000, θ₀, draw) # Run single threaded
# thetam = reduce(hcat, theta)'
@time thetalls = LowLevelParticleFilters.metropolis_threaded(burnin, ll, 5000, θ₀, draw) # run on all threads, will provide (2000-burnin)*nthreads() samples
histogram(exp.(thetalls[:,1:2]), layout=3)
plot!(thetalls[:,3], subplot=3) # if threaded call, log likelihoods are in the last column
```
