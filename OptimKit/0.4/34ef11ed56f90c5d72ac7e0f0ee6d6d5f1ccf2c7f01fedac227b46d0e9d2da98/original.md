```
struct ConjugateGradient{F<:CGFlavor,T<:Real,L<:AbstractLineSearch} <: OptimizationAlgorithm
ConjugateGradient(;
                  flavor::CGFlavor=HagerZhang(),
                  restart::Int=typemax(Int);
                  maxiter::Int=MAXITER[], # 1_000_000
                  gradtol::Real=GRADTOL[], # 1e-8
                  verbosity::Int=VERBOSITY[], # 1
                  ls_maxiter::Int=LS_MAXITER[], # 10
                  ls_maxfg::Int=LS_MAXFG[], # 20
                  ls_verbosity::Int=LS_VERBOSITY[], # 1
                  linesearch = HagerZhangLineSearch(maxiter=ls_maxiter, maxfg=ls_maxfg, verbosity=ls_verbosity))
```

ConjugateGradient optimization algorithm.

## Parameters

  * `flavor`: The flavor of the conjugate gradient algorithm (for selecting the β parameter; see below)
  * `restart::Int`: The number of iterations after which to reset the search direction.
  * `maxiter::Int`: The maximum number of iterations.
  * `gradtol::T`: The tolerance for the norm of the gradient.
  * `verbosity::Int`: The verbosity level of the optimization algorithm.
  * `ls_maxiter::Int`: The maximum number of iterations for the line search.
  * `ls_maxfg::Int`: The maximum number of function evaluations for the line search.
  * `ls_verbosity::Int`: The verbosity level of the line search algorithm.
  * `linesearch`: The line search algorithm to use; if a custom value is provided, it overrides `ls_maxiter`, `ls_maxfg`, and `ls_verbosity`.

Both verbosity levels use the following scheme:

  * 0: no output
  * 1: only warnings upon non-convergence
  * 2: convergence information at the end of the algorithm
  * 3: progress information after each iteration
  * 4: more detailed information (only for the linesearch)

The `flavor` parameter can take the values

  * `HagerZhang(; η::Real=4 // 10, θ::Real=1 // 1)`: Hager-Zhang formula for β
  * `HestenesStiefel(; pos = true)`: Hestenes-Stiefel formula for β
  * `FletcherReeves()`: Fletcher-Reeves formula for β
  * `PolakRibiere(; pos = true)`: Polak-Ribiere formula for β
  * `DaiYuan()`: Dai-Yuan formula for β
