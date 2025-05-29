```
saCL!(CH::ControlChart[; rlsim::Function, kw...])
```

Computes the control limit to satisfy the nominal properties of a control chart, using the stochastic approximation algorithm described in Capizzi and Masarotto (2016).

### Arguments

  * `CH` - A control chart.

### Keyword arguments

  * `rlsim` - A function that generates new data with signature `rlsim(CH; maxiter, delta)`. If left unspecified, defaults to `run_sim_sa`. See the help for `run_sim_sa` for more information about the requirements of the function.
  * `settings` - An `OptSettings` objects which contains variables that control the behaviour of the algorithm. See the `Accepted settings` section below for information about the settings that control the behaviour of the algorithm. For more information about the specifics of each keyword argument, see Capizzi and Masarotto (2016).
  * `Nfixed` - The number of iterations for the gain estimation stage (default: 500).
  * `Afixed` - The fixed gain during the gain estimation stage (default: 0.1).
  * `Amin` - The minimum allowed value of gain (default: 0.1).
  * `Amax` - The maximum allowed value of gain (default: 100.0).
  * `delta_sa` - The shift in control limit used during the gain estimation stage (default: 0.1).
  * `q` - The power that controls the denominator in the Robbins-Monro algorithm (default: 0.55).
  * `gamma` - The precision parameter for the stopping criterion of the algorithm (default: 0.02).
  * `Nmin` - The minimum number of iterations to avoid early terminations (default: 1000).
  * `z` - The quantile of the `Normal(0,1)` that controls the probability of the stopping criterion being satisfied (default: 3.0).
  * `Cmrl` - The inflation factor for the maximum number of iterations the run length may run for (default: 10.0).
  * `maxiter` - Maximum number of iterations before the algorithm is forcibly ended (default: 50000).
  * `verbose` - Whether to print information to the user about the state of the optimization (default: false).
  * `parallel::Bool` - Whether the algorithm should be run in parallel, using available threads (default: false). Parallelization is achieved by averaging `Threads.nthreads` independent replications of the algorithm, each with precision parameter `gamma*sqrt(Threads.nthreads)`. See [Capizzi, 2016] for further discussion on parallelizing the SA algorithm.

### Returns

  * A `NamedTuple` containing the estimated control limit `h`, the total number of iterations `iter`, and information `status` about the convergence of the algorithm.

### References

  * Capizzi, G., & Masarotto, G. (2016). "Efficient Control Chart Calibration by Simulated Stochastic Approximation". IIE Transactions 48 (1). https://doi.org/10.1080/0740817X.2015.1055392.
