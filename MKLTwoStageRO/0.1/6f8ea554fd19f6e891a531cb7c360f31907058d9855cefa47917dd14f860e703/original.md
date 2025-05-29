```
BDCP(Fields...)
```

Create an instance of the Benders-dual cutting plane (BDCP) algorithm (`Ref.1`).

# Fields

  * `MPsolver::Module = HiGHS`: The solver for the master problem (`MP`). It should be chosen based on the tpye of `Sy`. Generally, it should be an solver that supports mixed integer linear program (MILP) if `Sy` is a mixed integer space.
  * `SP1solver::Module = HiGHS`: The solver for the sub-problem in the KKT condition based reformulation (Bi/Tri-Equivalent I) form (`SP1`). Since `SP1` is a linearized reformulation based on big-M method, its solver should at least be an MILP solver, if `U` is just a polyhedral uncertainty set.
  * `SP2solver::Module = Ipopt`: The solver for the sub-problem in the strong duality based reformulation form (`SP2`). The function will always try to solve `SP1` first, and then move on to `SP2` if it fails. Since `SP2` is at least a bilinear optimization problem when `U` is a polyhedron, a solver that is tailored to this or roughly one that supports non-convex quadratic program (QP) is neccessary.
  * `SP2solver_max_iter::Integer = 10000`: The maximum limitation of iterations for `SP2solver` to solve `SP2`.
  * `ϵ::Real = 1e-5`: The overall absolute stopping criteria of the (nested) C&CG method. If the internal quadratic programming solver is active, it's also the tolorence of it.
  * `BigM::Real = 1e5`: The big-M value of `SP1` in its big-M method based linearized reformulation. Note that if a tight bound on big-M can be analytically obtained, a better performance of the algorithm can be achieved.
  * `verbose::Bool = true`: The switch that controls the output of the solution process details.

# Reference

1. Zeng, B., & Zhao, L. (2013). Solving two-stage robust optimization problems using a column-and-constraint generation method. Operations Research Letters, 41(5), 457-461.
