`OperatorCondition`

Specifies the assumption of matrix conditioning for the default linear solver choices. Condition number is defined as the ratio of eigenvalues. The numerical stability of many linear solver algorithms can be dependent on the condition number of the matrix. The condition number can be computed as:

```julia
using LinearAlgebra
cond(rand(100, 100))
```

However, in practice this computation is very expensive and thus not possible for most practical cases. Therefore, OperatorCondition lets one share to LinearSolve the expected conditioning. The higher the expected condition number, the safer the algorithm needs to be and thus there is a trade-off between numerical performance and stability. By default the method assumes the operator may be ill-conditioned for the standard linear solvers to converge (such as LU-factorization), though more extreme ill-conditioning or well-conditioning could be the case and specified through this assumption.
