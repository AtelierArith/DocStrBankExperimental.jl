```julia
continuation_hopf(
    prob_vf,
    alg,
    hopfpointguess,
    par,
    lens1,
    lens2,
    eigenvec,
    eigenvec_ad,
    options_cont;
    update_minaug_every_step,
    normC,
    linsolve_adjoint,
    bdlinsolver,
    bdlinsolver_adjoint,
    jacobian_ma,
    compute_eigen_elements,
    usehessian,
    kind,
    massmatrix,
    record_from_solution,
    kwargs...
)

```

codim 2 continuation of Hopf points. This function turns an initial guess for a Hopf point into a curve of Hopf points based on a Minimally Augmented formulation. The arguments are as follows

  * `prob::AbstractBifurcationProblem`
  * `hopfpointguess` initial guess (x*0, p1*0) for the Hopf point. It should be a `Vector` or a `BorderedArray`
  * `par` set of parameters
  * `lens1` parameter axis for parameter 1
  * `lens2` parameter axis for parameter 2
  * `eigenvec` guess for the iω eigenvector at p1_0
  * `eigenvec_ad` guess for the -iω eigenvector at p1_0
  * `options_cont` keywords arguments to be passed to the regular [`continuation`](@ref)

# Optional arguments:

  * `jacobian_ma::Symbol = :autodiff`, how the linear system of the Fold problem is solved. Can be `:autodiff, :finiteDifferencesMF, :finiteDifferences, :minaug`
  * `linsolve_adjoint` solver for (J+iω)^* ⋅sol = rhs
  * `bdlinsolver` bordered linear solver for the constraint equation with top-left block (J-iω). Required in the linear solver for the Minimally Augmented Hopf functional. This option can be used to pass a dedicated linear solver for example with specific preconditioner.
  * `bdlinsolver_adjoint` bordered linear solver for the constraint equation with top-left block (J-iω)^*. Required in the linear solver for the Minimally Augmented Hopf functional. This option can be used to pass a dedicated linear solver for example with specific preconditioner.
  * `update_minaug_every_step` update vectors `a,b` in Minimally Formulation every `update_minaug_every_step` steps
  * `compute_eigen_elements = false` whether to compute eigenelements. If `options_cont.detect_event>0`, it allows the detection of ZH, HH points.
  * `kwargs` keywords arguments to be passed to the regular [`continuation`](@ref)

# Simplified call:

```
continuation_hopf(br::AbstractBranchResult, ind_hopf::Int, lens2::AllOpticTypes, options_cont::ContinuationPar ;  kwargs...)
```

where the parameters are as above except that you have to pass the branch `br` from the result of a call to `continuation` with detection of bifurcations enabled and `index` is the index of Hopf point in `br` that you want to refine.

!!! tip "ODE problems"
    For ODE problems, it is more efficient to use the Matrix based Bordered Linear Solver passing the option `bdlinsolver = MatrixBLS()`. This is the default setting.


!!! tip "Jacobian transpose"
    The adjoint of the jacobian `J` is computed internally when `Jᵗ = nothing` by using `transpose(J)` which works fine when `J` is an `AbstractArray`. In this case, do not pass the jacobian adjoint like `Jᵗ = (x, p) -> transpose(d_xF(x, p))` otherwise the jacobian would be computed twice!


!!! tip "Detection of Bogdanov-Takens and Bautin bifurcations"
    In order to trigger the detection, pass `detect_event = 1,2` in `options_cont`. Note that you need to provide `d3F` in `prob`.

