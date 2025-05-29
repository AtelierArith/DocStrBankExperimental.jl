```
NLPModelMeta <: AbstractNLPModelMeta
```

A composite type that represents the main features of the optimization problem

```
optimize    obj(x)
subject to  lvar ≤    x    ≤ uvar
            lcon ≤ cons(x) ≤ ucon
```

where `x`        is an `nvar`-dimensional vector,       `obj`      is the real-valued objective function,       `cons`     is the vector-valued constraint function,       `optimize` is either "minimize" or "maximize".

Here, `lvar`, `uvar`, `lcon` and `ucon` are vectors. Some of their components may be infinite to indicate that the corresponding bound or general constraint is not present.

---

```
NLPModelMeta(nvar::Integer; kwargs...)
NLPModelMeta(meta::AbstractNLPModelMeta; kwargs...)
```

Create an `NLPModelMeta` with `nvar` variables. Alternatively, create an `NLPModelMeta` copy from another `AbstractNLPModelMeta`. The following keyword arguments are accepted:

  * `x0`: initial guess
  * `lvar`: vector of lower bounds
  * `uvar`: vector of upper bounds
  * `nlvb`: number of nonlinear variables in both objectives and constraints
  * `nlvo`: number of nonlinear variables in objectives (includes nlvb)
  * `nlvc`: number of nonlinear variables in constraints (includes nlvb)
  * `ncon`: number of general constraints
  * `y0`: initial Lagrange multipliers
  * `lcon`: vector of constraint lower bounds
  * `ucon`: vector of constraint upper bounds
  * `nnzo`: number of nonzeros in the gradient
  * `nnzj`: number of elements needed to store the nonzeros in the sparse Jacobian
  * `lin_nnzj`: number of elements needed to store the nonzeros in the sparse Jacobian of linear constraints
  * `nln_nnzj`: number of elements needed to store the nonzeros in the sparse Jacobian of nonlinear constraints
  * `nnzh`: number of elements needed to store the nonzeros in the sparse Hessian
  * `lin`: indices of linear constraints
  * `minimize`: true if optimize == minimize
  * `islp`: true if the problem is a linear program
  * `name`: problem name

`NLPModelMeta` also contains the following attributes, which are computed from the variables above:

  * `nvar`: number of variables
  * `ifix`: indices of fixed variables
  * `ilow`: indices of variables with lower bound only
  * `iupp`: indices of variables with upper bound only
  * `irng`: indices of variables with lower and upper bound (range)
  * `ifree`: indices of free variables
  * `iinf`: indices of visibly infeasible bounds
  * `jfix`: indices of equality constraints
  * `jlow`: indices of constraints of the form c(x) ≥ cl
  * `jupp`: indices of constraints of the form c(x) ≤ cu
  * `jrng`: indices of constraints of the form cl ≤ c(x) ≤ cu
  * `jfree`: indices of "free" constraints (there shouldn't be any)
  * `jinf`: indices of the visibly infeasible constraints
  * `nlin`: number of linear constraints
  * `nnln`: number of nonlinear general constraints
  * `nln`: indices of nonlinear constraints
