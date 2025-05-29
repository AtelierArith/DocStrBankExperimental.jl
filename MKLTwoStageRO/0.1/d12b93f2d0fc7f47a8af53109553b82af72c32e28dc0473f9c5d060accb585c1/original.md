```
ECCG(Fields...)
```

Create an instance of the Extended Column-and-Constraint Generation (ECCG) algorithm (`Ref.1`).

# Fields

  * `MPsolver::Module = HiGHS`: The solver for the master problem (`MP`). It should be chosen based on the tpyes of `Sx` and `Sy`. Generally, it should be an solver that supports mixed integer linear program (MILP) if `Sx` or `Sy` is a mixed integer space.
  * `SPsolver::Module = HiGHS`: The solver for the sub-problem (`SP`) in the KKT condition based reformulation form (both the feasiblity oracle and the optimality oracle). Since the sub-problem oracles are linearized reformulations based on big-M method, their solver should at least be an MILP solver, if `U` is just a polyhedral uncertainty set.
  * `ϵ::Real = 1e-5`: The overall absolute stopping criteria of the Extended CCG method. It's also used as the tolorence in the feasiblity oracle for which if the objective value of the oracle is not less than `ϵ` we then think the current `x` is infeasible.
  * `BigM::Real = 1e5`: The big-M value of `SP` in its big-M method based linearized reformulation (both the feasiblity oracle and the optimality oracle). Note that if a tight bound on big-M can be analytically obtained, a better performance of the algorithm can be achieved.
  * `verbose::Bool = true`: The switch that controls the output of the solution process details.

# Reference

1. Bertsimas, D., & Shtern, S. (2018). A scalable algorithm for two-stage adaptive linear optimization. arXiv preprint arXiv:1807.02812.
