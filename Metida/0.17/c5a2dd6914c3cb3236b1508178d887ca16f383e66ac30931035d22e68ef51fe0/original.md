```
fit!(lmm::LMM{T}; kwargs...
) where T
```

Fit LMM model.

# Keywords:

  * `solver` - :default / :nlopt for using with MetidaNLopt.jl/ :cuda for using with MetidaCu.jl
  * `verbose` - :auto / 1 / 2 / 3 - - 1 - only log,  2 - log and print,  3 - print only errors, other log, 0 (or any other value) - no logging
  * `varlinkf` - :exp / :sq / :identity [ref](@ref varlink_header)
  * `rholinkf` - :sigm / :atan / :sqsigm / :psigm
  * `aifirst` - first iteration with AI-like method - :default / :ai / :score
  * `aifmax` - maximum pre-optimization steps
  * `g_tol` - absolute tolerance in the gradient
  * `x_tol` - absolute tolerance of theta vector
  * `f_tol` - absolute tolerance in changes of the REML
  * `hes` - calculate REML Hessian
  * `init` - initial theta values
  * `io` - output IO
  * `time_limit` - time limit = 120 sec
  * `iterations` - maximum iterations = 300
  * `refitinit` - true/false - if `true` - use last values for initial condition  (`false` by default)
  * `optmethod` - Optimization method. Look at Optim.jl documentation. (Newton by default)
  * `singtol` - singular tolerance = 1e-8
  * `maxthreads` - maximum threads = min(num_cores(), Threads.nthreads())
