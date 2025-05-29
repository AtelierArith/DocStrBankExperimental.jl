```
spg_options(;verbose=3,optTol=1f-5,progTol=1f-7,
            maxIter=20,suffDec=1f-4,memory=2,
            useSpectral=true,curvilinear=false,
            feasibleInit=false,testOpt=true,
            bbType=true,testInit=false, store_trace=false,
            optNorm=Inf,iniStep=1f0, maxLinesearchIter=10)
```

Options structure for Spectral Project Gradient algorithm.

# Arguments

  * `verbose`: level of verbosity (0: no output, 1: iter (default))
  * `optTol`: tolerance used to check for optimality (default: 1e-5)
  * `progTol`: tolerance used to check for lack of progress (default: 1e-9)
  * `maxIter`: maximum number of iterations (default: 20)
  * `suffDec`: sufficient decrease parameter in Armijo condition (default: 1e-4)
  * `memory`: number of steps to look back in non-monotone Armijo condition
  * `useSpectral`: use spectral scaling of gradient direction (default: 1)
  * `curvilinear`: backtrack along projection Arc (default: 0)
  * `testOpt`: test optimality condition (default: 1)
  * `feasibleInit`: if 1, then the initial point is assumed to be feasible
  * `bbType`: type of Barzilai Borwein step (default: 1)
  * `testInit`: Whether to test the initial estimate for optimality (default: false)
  * `store_trace`: Whether to store the trace/history of x (default: false)
  * `optNorm`: First-Order Optimality Conditions norm (default: Inf)
  * `iniStep`: Initial step length estimate (default: 1)
  * `maxLinesearchIter`: Maximum number of line search iteration (default: 20)
