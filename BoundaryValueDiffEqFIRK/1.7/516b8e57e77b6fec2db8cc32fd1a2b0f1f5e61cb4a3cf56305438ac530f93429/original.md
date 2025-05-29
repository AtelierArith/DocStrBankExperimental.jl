```
  BoundaryValueDiffEqFIRK.RadauIIa1(; nlsolve = NewtonRaphson(), jac_alg = BVPJacobianAlgorithm(), nested_nlsolve = false, nest_tol = 0.0,
          defect_threshold = 0.1, max_num_subintervals = 3000)
```

1th stage RadauIIa method.

## Keyword Arguments

  * `nlsolve`: Internal Nonlinear solver. Any solver which conforms to the SciML `NonlinearProblem` interface can be used. Note that any autodiff argument for the solver will be ignored and a custom jacobian algorithm will be used.
  * `jac_alg`: Jacobian Algorithm used for the nonlinear solver. Defaults to `BVPJacobianAlgorithm()`, which automatically decides the best algorithm to use based on the input types and problem type.

      * For `TwoPointBVProblem`, only `diffmode` is used (defaults to `AutoSparse(AutoForwardDiff)` if possible else `AutoSparse(AutoFiniteDiff)`).
      * For `BVProblem`, `bc_diffmode` and `nonbc_diffmode` are used. For `nonbc_diffmode` defaults to `AutoSparse(AutoForwardDiff)` if possible else `AutoSparse(AutoFiniteDiff)`. For `bc_diffmode`, defaults to `AutoForwardDiff` if possible else `AutoFiniteDiff`.
  * `nested_nlsolve`: Whether or not to use a nested nonlinear solve for the implicit FIRK step. Defaults to `false`. If set to `false`, the FIRK stages are solved as a part of the global residual. The general recommendation is to choose `true` for larger problems and `false` for smaller ones.
  * `nest_tol`: The tolerance for the nested solver. Default is nothing which leads to `NonlinearSolve` automatically selecting the tolerance.
  * `defect_threshold`: Threshold for defect control.
  * `max_num_subintervals`: Number of maximal subintervals, default as 3000.

!!! note
    For type-stability, the chunksizes for ForwardDiff ADTypes in `BVPJacobianAlgorithm` must be provided.


## References

Reference for Lobatto and Radau methods:

```bibtex
@incollection{Jay2015,
    author="Jay, Laurent O.",
    editor="Engquist, Bj{"o}rn",
    title="Lobatto Methods",
    booktitle = {Encyclopedia of {Applied} and {Computational} {Mathematics}},
    year="2015",
    publisher="Springer Berlin Heidelberg",
}
@incollection{engquist_radau_2015,
    author = {Hairer, Ernst and Wanner, Gerhard},
    editor={Engquist, Bj{"o}rn},
    title = {Radau {Methods}},
    booktitle = {Encyclopedia of {Applied} and {Computational} {Mathematics}},
    publisher = {Springer Berlin Heidelberg},
    year = {2015},
}
```

References for implementation of defect control, based on the `bvp5c` solver in MATLAB:

```bibtex
@article{shampine_solving_nodate,
    title = {Solving {Boundary} {Value} {Problems} for {Ordinary} {Diﬀerential} {Equations} in {Matlab} with bvp4c
    author = {Shampine, Lawrence F and Kierzenka, Jacek and Reichelt, Mark W},
    year = {2000},
}

@article{kierzenka_bvp_2008,
    title = {A {BVP} {Solver} that {Controls} {Residual} and {Error}},
    author = {Kierzenka, J and Shampine, L F},
    year = {2008},
}

@article{russell_adaptive_1978,
    title = {Adaptive {Mesh} {Selection} {Strategies} for {Solving} {Boundary} {Value} {Problems}},
    journal = {SIAM Journal on Numerical Analysis},
    author = {Russell, R. D. and Christiansen, J.},
    year = {1978},
}
```
