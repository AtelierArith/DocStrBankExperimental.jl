```
check_model(pars, vals, c_, data_;
what=(:consistency, :derivatives, :optimization),
small=sqrt(eps()),
x0=[], lx=[], ux=[], x_scale=[],
precon=true,
visual=false,
rng=MersenneTwister(),
Hessian=true,
log10_rng=range(-6, -3, 10),
min_slope=0.9)
```

Tests, which any specific model should pass.

# Arguments

  * `pars::ModPar{T}`: Model parameters for constructor `create_model(pars)`.
  * `vals::Vector{Float64}`: *All* nonlinear parameters, the model depends on. As defined in the `Model` field `val`.
  * `c_::Vector{Nc, T}`: Linear cofficients, the model depends on.
  * `data_::AbstractArray`: Data, corresponding to the *true* parameters `vals` and `c_`, in a format suitable for `set_data!`.
  * `what::Tuple{Symbol}`: Tests to be performed (see below).
  * `small::Float64`: Required as accuracy criterion.
  * `x0::Vector{Float64}`: Starting point for optimization and location, where derivatives are tested.
  * `lx::Vector{Float64}`: Lower bound of optimization
  * `ux::Vector{Float64}`: Upper bound of optimization
  * `x_scale::Vector{Float64}`: Scaling vector, such that `δx = randn(size(x)) .* x_scale` becomes reasonable
  * `precon::Bool`: Test optimization with and without preconditioner.
  * `visual::Bool`: If `true` also generate double-logarithmic plots for the derivative tests.
  * `rng::MersenneTwister`: Allows to pass a unique seed (e.g. `MersenneTwister(42)`) for reproducible testing.
  * `Hessian::Bool`: Should be set to `false`, if the model does not implement second order derivatives.
  * `log10_rng::AbstractVector`: logarithmic range for derivative testing
  * `min_slope::Float64`: minimal derivative slope on log-log plot

## Remark

  * Tests are performed for every `x_sym ⊆ sym`.
  * Returns a dictionary with detailed information about the test results.
  * `:consistency ∈ what`: Several basic tests (parameters, names, correct model values)
  * `:derivatives ∈ what`: Check first and second order partial derivatives at `x0`.
  * `:optimization ∈ what`: Minimize model with `x0` as starting point and bounds `lx` and `ux`.
  * An example application can be found in [`test_BiExpDecay.jl`](https://github.com/cganter/VP4Optim.jl/blob/main/test/test_BiExpDecay.jl). This should also work as a template, how to perform tests on own models.
