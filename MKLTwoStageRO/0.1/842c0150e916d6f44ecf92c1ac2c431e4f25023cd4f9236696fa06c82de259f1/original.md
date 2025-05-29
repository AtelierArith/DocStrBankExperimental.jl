```
CCG(Fields...)
```

Create an instance of the (nested) column-and-constraint generation (C&CG) algorithm(`Ref.1-2`). If `Sx` is a nonnegative real-valued space, the algorithm (C&CG) from `Ref.1` will be called; if `Sx` is a nonnegative mixed integer space, the algorithm (Nested C&CG) from `Ref.2` will be called.

# Fields

  * `MPsolver::Module = HiGHS`: The solver for the master problem (`MP`). It should be chosen based on the tpyes of `Sy` and `Sx`. Generally, it should be an solver that supports mixed integer linear program (MILP) if `Sy` or `Sx` is a mixed integer space.
  * `SP1solver::Module = HiGHS`: The solver for the sub-problem in the KKT condition based reformulation (Bi/Tri-Equivalent I) form (`SP1`). Since `SP1` is a linearized reformulation based on big-M method, its solver should at least be an MILP solver, if `U` is just a polyhedral uncertainty set.
  * `SP2solver::Module = Ipopt`: This keyword argument is only available when `Sx` is a nonnegative real-valued space. It's the solver for the sub-problem in the strong duality based reformulation form (`SP2`). The function will always try to solve `SP1` first, and then move on to `SP2` if it fails. Since `SP2` is at least a bilinear optimization problem when `U` is a polyhedron, a solver that is tailored to this or roughly one that supports non-convex quadratic program (QP) is neccessary.
  * `SP2solver_max_iter::Integer = 10000`: This keyword argument is only available when `Sx` is a nonnegative real-valued space. It's the maximum limitation of iterations for `SP2solver` to solve `SP2`.
  * `SP2_MPsolver::Module = Ipopt`: This keyword argument is only available when `Sx` is a nonnegative mixed integer space. It's the solver for the master problem of the sub-problem in the strong duality based reformulation (Bi/Tri-Equivalent II) form (`SP2`). The function will always try to solve `SP1` first, and then move on to `SP2` if it fails. Since the master problem of `SP2` contains quadratic constraints even when `U` is just a polyhedral uncertainty set, an efficient solver that supports quadratically-constrained quadratic program (QCQP) is neccessary.
  * `SP2_MPsolver_max_iter::Integer = 10000`: This keyword argument is only available when `Sx` is a nonnegative mixed integer space. It's the maximum limitation of iterations for `SP2_MPsolver` to solve the master problem of `SP2`.
  * `SP2_SPsolver::Module = HiGHS`: This keyword argument is only available when `Sx` is a nonnegative mixed integer space.  It's the solver for the sub-problem of the sub-problem in the strong duality based reformulation (Bi/Tri-Equivalent II) form (`SP2`). The function will always try to solve `SP1` first, and then move on to `SP2` if it fails. The solver for the sub-problem of `SP2` only depends on the tpye of `Sx`, so it should be an MILP solver beacause of the mixed integer feature of `Sx`.
  * `ϵ::Real = 1e-5`: The overall absolute stopping criteria of the (nested) C&CG method. If the internal quadratic programming solver is active, it's also the tolorence of it.
  * `BigM::Real = 1e5`: The big-M value of `SP1` in its big-M method based linearized reformulation. Note that if a tight bound on big-M can be analytically obtained, a better performance of the algorithm can be achieved.
  * `verbose::Bool = true`: The switch that controls the output of the solution process details.

# References

1. Zeng, B., & Zhao, L. (2013). Solving two-stage robust optimization problems using a column-and-constraint generation method. Operations Research Letters, 41(5), 457-461.
2. Zhao, L., & Zeng, B. (2012). An exact algorithm for two-stage robust optimization with mixed integer recourse problems. submitted, available on Optimization-Online. org.
