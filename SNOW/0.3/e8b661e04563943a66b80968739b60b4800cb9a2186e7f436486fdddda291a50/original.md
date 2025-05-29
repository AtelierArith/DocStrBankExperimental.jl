```
Options(;sparsity=DensePattern(), derivatives=ForwardFD(), solver=IPOPT())
```

Options for SNOW.  Default is dense, forward finite differencing, and IPOPT.

# Arguments

  * `sparsity::AbstractSparsityPattern`: specify sparsity pattern
  * `derivatives::AbstractDiffMethod`: specific differentiation methods to use   or `derivatives::Vector{AbstractDiffMethod}`: vector of length two,    first for gradient differentiation method, second for jacobian differentiation method
  * `solver::AbstractSolver`: specificy which optimizer to use
