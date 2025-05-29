```
LBFGS(m::Int = 8; 
      acceptfirst::Bool = true,
      maxiter::Int=MAXITER[], # 1_000_000
      gradtol::Real=GRADTOL[], # 1e-8
      verbosity::Int=VERBOSITY[], # 1
      ls_maxiter::Int=LS_MAXITER[], # 10
      ls_maxfg::Int=LS_MAXFG[], # 20
      ls_verbosity::Int=LS_VERBOSITY[], # 1
      linesearch = HagerZhangLineSearch(maxiter=ls_maxiter, maxfg=ls_maxfg, verbosity=ls_verbosity))
```

LBFGS optimization algorithm.

## Parameters

  * `m::Int`: The number of previous iterations to store for the limited memory BFGS approximation.
  * `maxiter::Int`: The maximum number of iterations.
  * `gradtol::T`: The tolerance for the norm of the gradient.
  * `verbosity::Int`: The verbosity level of the optimization algorithm.
  * `acceptfirst::Bool`: Whether to accept the first step of the line search.
  * `ls_maxiter::Int`: The maximum number of iterations for the line search.
  * `ls_maxfg::Int`: The maximum number of function evaluations for the line search.
  * `ls_verbosity::Int`: The verbosity level of the line search algorithm.
  * `linesearch`: The line search algorithm to use; if a custom value is provided, it overrides `ls_maxiter`, `ls_maxfg`, and `ls_verbosity`.

Both `verbosity` and `ls_verbosity` use the following scheme:

  * 0: no output
  * 1: only warnings upon non-convergence
  * 2: convergence information at the end of the algorithm
  * 3: progress information after each iteration
  * 4: more detailed information (only for the linesearch)
