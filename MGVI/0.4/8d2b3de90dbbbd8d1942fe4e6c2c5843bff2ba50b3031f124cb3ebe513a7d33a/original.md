```
struct ResidualSampler
```

Generates zero-centered samples from the posterior's covariance approximated by the Fisher information.

This sampler uses Conjugate Gradients to iteratively invert  the Fisher information, never instantiating the covariance in memory explicitly.

The Fisher information in canonical coordinates and Jacobian of the coordinate transformation are provided as arguments.

Constructor:

```julia
ResidualSampler(f_model::Function, center_point::Vector{<:Real}, linear_solver, context::MGVIContext)
```

`linear_solver` must be a solver supported by [`LinearSolve`](https://github.com/SciML/LinearSolve.jl) or [`MGVI.MatrixInversion`](@ref). Use `MatrixInversion` only for low-dimensional problems.

Call `MGVI.sample_residuals(s::ResidualSampler[, n::Integer])` to generate a single or `n` samples.
