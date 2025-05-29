```julia
continuation_potrap(
    prob,
    orbitguess,
    alg,
    contParams,
    linear_algo;
    eigsolver,
    record_from_solution,
    plot_solution,
    kwargs...
)

```

This is the continuation routine for computing a periodic orbit using a functional G based on Finite Differences and a Trapezoidal rule.

# Arguments

  * `prob::PeriodicOrbitTrapProblem` encodes the functional G
  * `orbitguess` a guess for the periodic orbit where `orbitguess[end]` is an estimate of the period of the orbit. It could be a vector of size `N * M + 1` where `M` is the number of time slices, `N` is the dimension of the phase space. This must be compatible with the numbers `N, M` in `prob`.
  * `alg` continuation algorithm
  * `contParams` same as for the regular [`continuation`](@ref) method
  * `linear_algo` same as in [`continuation`](@ref)

# Keywords arguments

  * `eigsolver` specify an eigen solver for the computation of the Floquet exponents, defaults to `FloquetQaD`

Specify the choice of the jacobian (and linear algorithm), `jacobian` must belong to `[:FullLU, :FullSparseInplace, :Dense, :DenseAD, :BorderedLU, :BorderedSparseInplace, :FullMatrixFree, :BorderedMatrixFree, :FullMatrixFreeAD]`. This is used to select a way of inverting the jacobian `dG` of the functional G.

  * For `jacobian = :FullLU`, we use the default linear solver based on a sparse matrix representation of `dG`. This matrix is assembled at each newton iteration. This is the default algorithm.
  * For `jacobian = :FullSparseInplace`, this is the same as for `:FullLU` but the sparse matrix `dG` is updated inplace. This method allocates much less. In some cases, this is significantly faster than using `:FullLU`. Note that this method can only be used if the sparsity pattern of the jacobian is always the same.
  * For `jacobian = :Dense`, same as above but the matrix `dG` is dense. It is also updated inplace. This option is useful to study ODE of small dimension.
  * For `jacobian = :DenseAD`, evaluate the jacobian using ForwardDiff
  * For `jacobian = :BorderedLU`, we take advantage of the bordered shape of the linear solver and use a LU decomposition to invert `dG` using a bordered linear solver.
  * For `jacobian = :BorderedSparseInplace`, this is the same as for `:BorderedLU` but the cyclic matrix `dG` is updated inplace. This method allocates much less. In some cases, this is significantly faster than using `:BorderedLU`. Note that this method can only be used if the sparsity pattern of the jacobian is always the same.
  * For `jacobian = :FullMatrixFree`, a matrix free linear solver is used for `dG`: note that a preconditioner is very likely required here because of the cyclic shape of `dG` which affects negatively the convergence properties of GMRES.
  * For `jacobian = :BorderedMatrixFree`, a matrix free linear solver is used but for `Jc` only (see docs): it means that `options.linsolver` is used to invert `Jc`. These two Matrix-Free options thus expose different part of the jacobian `dG` in order to use specific preconditioners. For example, an ILU preconditioner on `Jc` could remove the constraints in `dG` and lead to poor convergence. Of course, for these last two methods, a preconditioner is likely to be required.
  * For `jacobian = :FullMatrixFreeAD`, the evaluation map of the differential is derived using automatic differentiation. Thus, unlike the previous two cases, the user does not need to pass a Matrix-Free differential.

Note that by default, the method prints the period of the periodic orbit as function of the parameter. This can be changed by providing your `record_from_solution` argument.
