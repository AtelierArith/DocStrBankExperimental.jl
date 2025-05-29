```julia
continuation(br, ind_bif, lens2; ...)
continuation(
    br,
    ind_bif,
    lens2,
    options_cont;
    prob,
    start_with_eigen,
    detect_codim2_bifurcation,
    update_minaug_every_step,
    kwargs...
)

```

Codimension 2 continuation of Fold / Hopf points. This function turns an initial guess for a Fold / Hopf point into a curve of Fold / Hopf points based on a Minimally Augmented formulation. The arguments are as follows

  * `br` results returned after a call to [continuation](@ref Library-Continuation)
  * `ind_bif` bifurcation index in `br`
  * `lens2` second parameter used for the continuation, the first one is the one used to compute `br`, e.g. `getlens(br)`
  * `options_cont = br.contparams` arguments to be passed to the regular [continuation](@ref Library-Continuation)

# Optional arguments:

  * `linsolve_adjoint` solver for (J+iω)˟ ⋅sol = rhs or Jᵗ ⋅sol = rhs
  * `bdlinsolver` bordered linear solver for the constraint equation
  * `bdlinsolver_adjoint` bordered linear solver for the constraint equation with top-left block (J-iω)˟ or Jᵗ. Required in the linear solver for the Minimally Augmented Fold/Hopf functional. This option can be used to pass a dedicated linear solver for example with specific preconditioner.
  * `update_minaug_every_step` update vectors `a, b` in Minimally Formulation every `update_minaug_every_step` steps
  * `detect_codim2_bifurcation ∈ {0,1,2}` whether to detect Bogdanov-Takens, Bautin and Cusp. If equals `1` non precise detection is used. If equals `2`, a bisection method is used to locate the bifurcations. Default value = 2.
  * `start_with_eigen = false` whether to start the Minimally Augmented problem with information from eigen elements. If `start_with_eigen = false`, then:

      * `a::Nothing` estimate of null vector of J (resp. J-iω) for Fold (resp. Hopf). If nothing is passed, a random vector is used. In case you do not rely on `AbstractArray`, you should probably pass this.
      * `b::Nothing` estimate of null vector of Jᵗ (resp. (J-iω)˟) for Fold (resp. Hopf). If nothing is passed, a random vector is used. In case you do not rely on `AbstractArray`, you should probably pass this.
  * `kwargs` keywords arguments to be passed to the regular [continuation](@ref Library-Continuation)

where the parameters are as above except that you have to pass the branch `br` from the result of a call to `continuation` with detection of bifurcations enabled and `index` is the index of Hopf point in `br` you want to refine.

!!! tip "ODE problems"
    For ODE problems, it is more efficient to use the Matrix based Bordered Linear Solver passing the option `bdlinsolver = MatrixBLS()`


!!! tip "start_with_eigen"
    It is recommended that you use the option `start_with_eigen = true`

