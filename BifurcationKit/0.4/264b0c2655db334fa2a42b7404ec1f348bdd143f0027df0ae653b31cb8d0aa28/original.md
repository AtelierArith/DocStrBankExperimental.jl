```julia
newton(
    br,
    ind_bif;
    normN,
    options,
    start_with_eigen,
    lens2,
    kwargs...
)

```

This function turns an initial guess for a Fold / Hopf point into a solution to the Fold / Hopf problem based on a Minimally Augmented formulation.

## Arguments

  * `br` results returned after a call to [continuation](@ref Library-Continuation)
  * `ind_bif` bifurcation index in `br`

# Optional arguments:

  * `options::NewtonPar`, default value `br.contparams.newton_options`
  * `normN = norm`
  * `options` You can pass newton parameters different from the ones stored in `br` by using this argument `options`.
  * `bdlinsolver` bordered linear solver for the constraint equation
  * `start_with_eigen = false` whether to start the Minimally Augmented problem with information from eigen elements.
  * `kwargs` keywords arguments to be passed to the regular Newton-Krylov solver

!!! tip "ODE problems"
    For ODE problems, it is more efficient to use the Matrix based Bordered Linear Solver passing the option `bdlinsolver = MatrixBLS()`


!!! tip "start_with_eigen"
    It is recommended that you use the option `start_with_eigen=true`

