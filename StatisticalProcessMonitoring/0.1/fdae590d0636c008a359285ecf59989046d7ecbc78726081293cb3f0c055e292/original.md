```
bisectionCL!(CH::ControlChart, hmax[; rlsim::Function, kw...])
```

Computes the control limit to satisfy the nominal properties of a control chart, using the bisection algorithm (see for instance Qiu, 2013)

### Arguments

  * `CH` - A control chart.
  * `hmax` - The maximum value for the control limit.

### Keyword arguments

  * `rlsim` - A function that generates a run length for the control chart with signature `rlsim(CH; maxiter)`. If left unspecified, defaults to `run_sim`. See the help for `run_sim` for more information about the signature of the function.
  * `nsims` - The number of run lengths used to estimate the target nominal property (default: 10000).
  * `hmin` - The minimum value of the control limit, (default: `sqrt(eps())`).
  * `maxiter` - The maximum number of bisection iterations (default: 30).
  * `maxrl` - The value at which to maxrlate the run length, to avoid excessive computations (default: Inf, i.e. no maxrlation).
  * `x_tol` - Absolute tolerance for the algorithm, which is terminated if   $h^{(k+1)} - h^{(k)} < x_{\text{tol}}$   (default: 1e-06)
  * `f_tol` - Absolute tolerance for the algorithm, which is terminated if   $\text{target}(h^{(k+1)}) - \text{target}(h^{(k)}) < f_{\text{tol}}$   (default: 1.0)
  * `verbose` - Whether to print information to the user about the state of the optimization (default: false).
  * `parallel::Bool` - Whether the algorithm should be run in parallel, using available threads (default: false)

### Returns

  * A `NamedTuple` containing the estimated control limit `h`, the total number of iterations `iter`, and information `status` about the convergence of the algorithm.

### References

  * Qiu, P. (2013). Introduction to Statistical Process Control. Boca Raton: CRC Press.
