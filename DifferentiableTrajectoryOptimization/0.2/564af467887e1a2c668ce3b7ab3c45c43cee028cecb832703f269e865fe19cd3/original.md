A solver backend that treats the problem as a quadratic program (QP)

```
QP(y) := argmin_x 0.5 x'Qx + x'(Ry+q)
         s.t.  lb <= Ax + By <= ub
```

# Note

Here, the problem data tuple `(Q, R, q A, B, lb, ub)` is derived from the provided `ParametricTrajectoryOptimizationProblem` via linearization of constraints and quadraticization of the objective. Therefore, if the problem is not a QP then this solution is not exact!
