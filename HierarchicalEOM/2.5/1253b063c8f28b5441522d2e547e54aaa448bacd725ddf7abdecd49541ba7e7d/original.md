```
Propagator(M, Δt; threshold, nonzero_tol)
```

Use `FastExpm.jl` to calculate the propagator matrix from a given HEOM Liouvillian superoperator matrix $M$ with a specific time step $\Delta t$. That is, $\exp(M * \Delta t)$.

# Parameters

  * `M::AbstractHEOMLSMatrix` : the matrix given from HEOM model
  * `Δt::Real` : A specific time step (time interval).
  * `threshold::Real` : Determines the threshold for the Taylor series. Defaults to `1.0e-6`.
  * `nonzero_tol::Real` : Strips elements smaller than `nonzero_tol` at each computation step to preserve sparsity. Defaults to `1.0e-14`.

For more details, please refer to [`FastExpm.jl`](https://github.com/fmentink/FastExpm.jl)

# Returns

  * `::SparseMatrixCSC{ComplexF64, Int64}` : the propagator matrix
