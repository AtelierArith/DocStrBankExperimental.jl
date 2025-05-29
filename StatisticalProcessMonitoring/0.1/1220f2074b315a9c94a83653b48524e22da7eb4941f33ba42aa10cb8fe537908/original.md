```
bootstrapCL!(CH::ControlChart[; rlsim::Function, kw...])
```

Computes the control limit to satisfy the nominal properties of a control chart, using the bisection algorithm on bootstrapped paths (see for instance Qiu, 2013).

### Arguments

  * `CH` - A control chart.

### Keyword arguments

  * `rlsim` - A function that generates a path of the control chart statistic with signature `rlsim(CH; maxiter)`. If left unspecified, defaults to `run_path_sim`. See the help for `run_path_sim` for more information about the signature of the function.
  * `settings` - An `OptSettings` objects which contains variables that control the behaviour of the algorithm. See the `Accepted settings` section below for information about the settings that control the behaviour of the algorithm. For more information about the specifics of each keyword argument, see for instance Qiu (2013).
  * `maxiter` - The maximum number of bisection iterations.
  * `nsims` - The number of run lengths used to estimate the target nominal property.
  * `maxrl` - The maximum run length after which the run length is truncated, to avoid excessive computations.
  * `x_tol` - Absolute tolerance for the algorithm, which is ended if   $h^{(k+1)} - h^{(k)} < x_{\text{tol}}$
  * `f_tol` - Absolute tolerance for the algorithm, which is ended if   $\text{target}(h^{(k+1)}) - \text{target}(h^{(k)}) < f_{\text{tol}}$

### Returns

  * A `NamedTuple` containing the estimated control limit `h`, the total number of iterations `iter`, and information `status` about the convergence of the algorithm.

### References

  * Qiu, P. (2013). Introduction to Statistical Process Control. Boca Raton: CRC Press.
