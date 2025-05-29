```
combinedCL!(CH::ControlChart[; rlsim::Function, kw...])
```

Computes the control limit to satisfy the nominal properties of a control chart, using the bisection algorithm (see for instance Qiu, 2013). The control limit upper bound `hmax` for the bisection algorithm is found using the stochastic approximation algorithm of Capizzi and Masarotto (2016)

### Arguments

  * `CH` - A control chart.

### Keyword arguments

  * `inflate::Real` - An inflation constant for the starting control limit value so that, on average, the first iteration will move the control limit to lower values. This usually saves computational time (default: 1.05).
  * `parallel::Bool` - Whether the algorithm should be run in parallel, using available threads (default: false)

#### Bisection algorithm

  * `rlsim` - A function that generates a run length for the control chart with signature `rlsim(CH; maxiter)`. If left unspecified, defaults to `run_sim`. See the help for `run_sim` for more information about the signature of the function.
  * `nsims` - The number of run lengths used to estimate the target nominal property (default: 10000).
  * `hmin` - The minimum value of the control limit, (default: `sqrt(eps())`).
  * `maxiter` - The maximum number of bisection iterations (default: 30).
  * `maxrl` - The value at which to maxrlate the run length, to avoid excessive computations (default: Inf, i.e. no maxrlation).
  * `x_tol` - Absolute tolerance for the algorithm, which is terminated if   $h^{(k+1)} - h^{(k)} < x_{\text{tol}}$   (default: 1e-06)
  * `f_tol` - Absolute tolerance for the algorithm, which is terminated if   $\text{target}(h^{(k+1)}) - \text{target}(h^{(k)}) < f_{\text{tol}}$   (default: 1.0)

#### SA algorithm

  * `Nfixed` - The number of iterations for the gain estimation stage (default: 200).
  * `Afixed` - The fixed gain during the gain estimation stage (default: 0.1).
  * `Amin` - The minimum allowed value of gain (default: 0.1).
  * `Amax` - The maximum allowed value of gain (default: 100).
  * `deltaSA` - The shift in control limit used during the gain estimation stage (default: 0.1).
  * `q` - The power that controls the denominator in the Robbins-Monro algorithm (default: 0.55).
  * `gamma` - The precision parameter for the stopping criterion of the algorithm (default: 0.05).
  * `Nmin` - The minimum number of iterations required for the algorithm to end (default: 200).
  * `z` - The quantile of the `Normal(0,1)` that controls the probability of the stopping criterion being satisfied (default: 3.0).
  * `Cmrl` - The inflation factor for the maximum number of iterations the run length may run for (default: 10.0).
  * `maxiter_sa` - Maximum number of iterations before the algorithm is forcibly ended (default: 200).
  * `verbose` - Whether to print information to the user about the state of the optimization (default: false).

### Returns

  * A `NamedTuple` containing the estimated control limit `h`, the total number of iterations `iter`, and information `status` about the convergence of the algorithm.

### References

  * Qiu, P. (2013). Introduction to Statistical Process Control. Boca Raton: CRC Press.
  * Capizzi, G., & Masarotto, G. (2016). Efficient control chart calibration by simulated stochastic approximation. IIE Transactions, 48(1), 57-65. https://doi.org/10.1080/0740817X.2015.1055392
