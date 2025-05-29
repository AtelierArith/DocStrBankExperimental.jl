```julia
newton_hopf(
    prob,
    hopfpointguess,
    par,
    eigenvec,
    eigenvec_ad,
    options;
    normN,
    bdlinsolver,
    usehessian,
    kwargs...
)

```

This function turns an initial guess for a Hopf point into a solution to the Hopf problem based on a Minimally Augmented formulation. The arguments are as follows

  * `prob::AbstractBifurcationProblem` where `p` is a set of parameters.
  * `hopfpointguess` initial guess (x*0, p*0) for the Hopf point. It should a `BorderedArray` as returned by the function `HopfPoint`.
  * `par` parameters used for the vector field
  * `eigenvec` guess for the  iω eigenvector
  * `eigenvec_ad` guess for the -iω eigenvector
  * `options::NewtonPar` options for the Newton-Krylov algorithm, see [`NewtonPar`](@ref).

# Optional arguments:

  * `normN = norm`
  * `bdlinsolver` bordered linear solver for the constraint equation
  * `kwargs` keywords arguments to be passed to the regular Newton-Krylov solver

# Simplified call:

Simplified call to refine an initial guess for a Hopf point. More precisely, the call is as follows

```
newton_hopf(br::AbstractBranchResult, ind_hopf::Int; normN = norm, options = br.contparams.newton_options, kwargs...)
```

The parameters / options are as usual except that you have to pass the branch `br` from the result of a call to `continuation` with detection of bifurcations enabled and `index` is the index of bifurcation point in `br` you want to refine. You can pass newton parameters different from the ones stored in `br` by using the argument `options`.

!!! tip "Jacobian transpose"
    The adjoint of the jacobian `J` is computed internally when `Jᵗ = nothing` by using `transpose(J)` which works fine when `J` is an `AbstractArray`. In this case, do not pass the jacobian adjoint like `Jᵗ = (x, p) -> transpose(d_xF(x, p))` otherwise the jacobian will be computed twice!


!!! tip "ODE problems"
    For ODE problems, it is more efficient to use the Matrix based Bordered Linear Solver passing the option `bdlinsolver = MatrixBLS()`

