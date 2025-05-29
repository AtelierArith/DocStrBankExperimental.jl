```julia
continuation_fold(
    prob,
    alg,
    foldpointguess,
    par,
    lens1,
    lens2,
    eigenvec,
    eigenvec_ad,
    options_cont;
    update_minaug_every_step,
    normC,
    bdlinsolver,
    bdlinsolver_adjoint,
    jacobian_ma,
    compute_eigen_elements,
    usehessian,
    kind,
    record_from_solution,
    kwargs...
)

```

Codim 2 continuation of Fold points. This function turns an initial guess for a Fold point into a curve of Fold points based on a Minimally Augmented formulation. The arguments are as follows

  * `prob::AbstractBifurcationFunction`
  * `foldpointguess` initial guess (x*0, p1*0) for the Fold point. It should be a `BorderedArray` as returned by the function `foldpoint`
  * `par` set of parameters
  * `lens1` parameter axis for parameter 1
  * `lens2` parameter axis for parameter 2
  * `eigenvec` guess for the right null vector
  * `eigenvec_ad` guess for the left null vector
  * `options_cont` arguments to be passed to the regular [`continuation`](@ref)

# Optional arguments:

  * `jacobian_ma::Symbol = :autodiff`, how the linear system of the Fold problem is solved. Can be `:autodiff, :finiteDifferencesMF, :finiteDifferences, :minaug`
  * `bdlinsolver` bordered linear solver for the constraint equation with top-left block J. Required in the linear solver for the Minimally Augmented Fold functional. This option can be used to pass a dedicated linear solver for example with specific preconditioner.
  * `bdlinsolver_adjoint` bordered linear solver for the constraint equation with top-left block J^*. Required in the linear solver for the Minimally Augmented Fold functional. This option can be used to pass a dedicated linear solver for example with specific preconditioner.
  * `update_minaug_every_step` update vectors `a, b` in Minimally Formulation every `update_minaug_every_step` steps
  * `compute_eigen_elements = false` whether to compute eigenelements. If `options_cont.detect_event>0`, it allows the detection of ZH points.
  * `kwargs` keywords arguments to be passed to the regular [`continuation`](@ref)

# Simplified call

```
continuation_fold(br::AbstractBranchResult, ind_fold::Int64, lens2::AllOpticTypes, options_cont::ContinuationPar ; kwargs...)
```

where the parameters are as above except that you have to pass the branch `br` from the result of a call to `continuation` with detection of bifurcations enabled and `index` is the index of Fold point in `br` that you want to continue.

!!! tip "Jacobian transpose"
    The adjoint of the jacobian `J` is computed internally when `Jᵗ = nothing` by using `transpose(J)` which works fine when `J` is an `AbstractArray`. In this case, do not pass the jacobian adjoint like `Jᵗ = (x, p) -> transpose(d_xF(x, p))` otherwise the jacobian would be computed twice!


!!! tip "ODE problems"
    For ODE problems, it is more efficient to use the Matrix based Bordered Linear Solver passing the option `bdlinsolver = MatrixBLS()`. This is the default setting.


!!! tip "Detection of Bogdanov-Takens and Cusp bifurcations"
    In order to trigger the detection, pass `detect_event = 1 or 2` in `options_cont`.

