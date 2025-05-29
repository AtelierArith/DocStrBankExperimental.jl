```
function DE(;
    n_groups = 4, 
    priors = nothing, 
    Np, 
    burnin = 1000, 
    discard_burnin = true, 
    α = .1,
    β = .1, 
    ϵ = .001,
    σ = .05, 
    κ = 1.0, 
    θsnooker = 0.0, 
    bounds, 
    n_initial = 0, 
    generate_proposal = random_gamma, 
    update_particle! = mh_update!,
    evaluate_fitness! = compute_posterior!, 
    sample = sample,
    blocking_on = x -> false,
    blocks = [false])
```

Differential Evolution MCMC object.

# Keywords

  * `n_groups=4`: number of groups of particles.
  * `Np`: number of particles per group.
  * `burnin=1000`: number of burnin iterations
  * `discard_burnin`: indicates whether burnin samples are discarded. Default is true.
  * `α=.1`: migration probability.
  * `β=.1`: mutation probability.
  * `ϵ=.001`: noise in crossover step.
  * `σ=.05`: standard deviation of noise added to parameters for mutation.
  * `κ=1.0`: recombination with probability (1-κ) during crossover.
  * `θsnooker=0`: sample along line x_i - z. 0.1 is recommended if > 0.
  * `n_initial`: initial number of samples from the prior distribution when `sample=resample`. 10 times the number of parameters is a typical value
  * `bounds`: a vector of tuples for lower and upper bounds of each parameter
  * `iter`: current iteration
  * `generate_proposal`: a function that generates proposals. Default is the two mode proposal described in Turner et al. 2012. You can also choose `fixed_gamma`, `variable_gamma` (see help) or pass a custom function
  * `update_particle!`: a function for updating the particle with a proposal value. Default: `mh_update!`, which uses the Metropolis-Hastings rule.
  * `evaluate_fitness!`: a function for evaluating the fitness of a posterior. The default is to compute the posterior loglikelihood with `compute_posterior!`. Select `evaluate_fun!` for optimization rather than MCMC sampling.
  * `sample`: a function for sampling particles during the crossover step. The default `sample` uses current particle parameter values whereas `resample` samples from the history of accepted values for each particle. Np must 3 or greater when using `resample`.
  * `blocking_on = x -> false`: a function that indicates whether block updating is used on each iteration. The function requires optimization_tests arguement for the DE sampler object and must return a true or false value.
  * `blocks`: a vector of boolean vectors indicating which parameters to update. Each sub-vector represents a block and each element in the sub-vector indicates which parameters are updated within the block. For example, [[true,false],[false,true]] indicates that the parameter in the first position is updated on the first block and the parameter in the second position is updated on the second block. If a parameter is a vector or matrix, they are nested within the block sub-vector.

# References

  * Ter Braak, C. J. A Markov Chain Monte Carlo version of the genetic algorithm Differential Evolution: easy Bayesian computing for real parameter spaces.
  * Ter Braak, Cajo JF, and Jasper A. Vrugt. Differential evolution Markov chain with snooker updater and fewer chains. Statistics and Computing 18.4 (2008): 435-446
  * Turner, B. M., Sederberg, P. B., Brown, S. D., & Steyvers, M. (2013). A method for efficiently sampling from distributions with correlated dimensions. Psychological methods, 18(3), 368.
  * Turner, B. M., & Sederberg, P. B. (2012). Approximate Bayesian computation with differential evolution. Journal of Mathematical Psychology, 56(5), 375-385.
