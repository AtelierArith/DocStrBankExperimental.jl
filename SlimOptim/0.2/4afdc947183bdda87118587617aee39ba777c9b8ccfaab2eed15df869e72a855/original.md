```
pqn_options(;verbose=2, optTol=1f-5, progTol=1f-7,
            maxIter=20, suffDec=1f-4, corrections=10, adjustStep=false,
            bbInit=false, store_trace=false, SPGoptTol=1f-6, SPGprogTol=1f-7,
            SPGiters=10, SPGtestOpt=false, maxLinesearchIter=20)
```

Options structure for Spectral Project Gradient algorithm.

# Arguments

  * `verbose`: level of verbosity (0: no output, 1: iter (default))
  * `optTol`: tolerance used to check for optimality (default: 1e-5)
  * `progTol`: tolerance used to check for progress (default: 1e-9)
  * `maxIter`: maximum number of iterations (default: 20)
  * `suffDec`: sufficient decrease parameter in Armijo condition (default: 1e-4)
  * `corrections`: number of lbfgs corrections to store (default: 10)
  * `adjustStep`: use quadratic initialization of line search (default: 0)
  * `bbInit`: initialize sub-problem with Barzilai-Borwein step (default: 1)
  * `store_trace`: Whether to store the trace/history of x (default: false)
  * `SPGoptTol`: optimality tolerance for SPG direction finding (default: 1e-6)
  * `SPGprogTol`: SPG tolerance used to check for progress (default: 1e-7)
  * `SPGiters`: maximum number of iterations for SPG direction finding (default:10)
  * `SPGtestOpt`: Whether to check for optimality in SPG (default: false)
  * `maxLinesearchIter`: Maximum number of line search iteration (default: 20)
  * `memory`: Number of steps for the non-monotone functional decrease condition.
  * `iniStep`: Initial step length estimate (default: 1). Ignored with adjustStep.
