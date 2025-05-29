```
bregman_options(;verbose=1, optTol=1e-6, progTol=1e-8, maxIter=20,
                store_trace=false, quantile=.5, alpha=.25, spg=false)
```

Options structure for the bregman iteration algorithm

# Arguments

  * `verbose`: level of verbosity (0: no output, 1: final, 2: iter (default), 3: debug)
  * `progTol`: tolerance used to check for lack of progress (default: 1e-9)
  * `maxIter`: maximum number of iterations (default: 20)
  * `store_trace`: Whether to store the trace/history of x (default: false)
  * `antichatter`: Whether to use anti-chatter step length correction
  * `alpha`: Strong convexity modulus. (step length is $α \frac{||r||_2^2}{||g||_2^2}$)
  * `spg`: whether to use spg, default is false
  * `TD`: sparsifying transform (e.g. curvelet), default is identity (LinearAlgebra.I)
  * `λfunc`: a function to calculate threshold value, default is nothing
  * `λ`: a pre-set threshold, will only be used if `λfunc` is not defined, default is nothing
  * `quantile`: a percentage to calculate the threshold by quantile of the dual variable in 1st iteration, will only be used if neither `λfunc` nor `λ` are defined, default is .95 i.e thresholds 95% of the vector
  * `w`: a weight vector that is applied on the threshold element-wise according to relaxation of weighted l1, default is 1 (no weighting)
  * `reset_lambda`: How often should lambda be updated. Defaults to `nothing` i.e lambda is nerver updated and estimated at the first iteration.
