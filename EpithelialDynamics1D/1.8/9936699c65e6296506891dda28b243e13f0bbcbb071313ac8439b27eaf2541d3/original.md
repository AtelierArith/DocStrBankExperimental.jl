```
CellProblem{F,DF,DP,G,GP}
```

Struct for representing a cell simulation problem. 

# Fields

  * `force_law::F`: The force law, e.g. `(δ, p) -> p.k * (p.s - δ)`.
  * `force_law_parameters::Fp`: The parameters for the force law.
  * `proliferation_law::G = (δ, p) -> zero(δ)`: The proliferation law, e.g. `(δ, p) -> p.β`.
  * `proliferation_law_parameters::Gp = nothing`: The parameters for the proliferation law.
  * `proliferation_period::Float64 = 1e-2`: How often to attempt a proliferation event.
  * `initial_time::Float64 = 0.0`: The initial time.
  * `final_time::Float64`: The final time.
  * `fix_left::Bool = true`: Whether to fix the left endpoint.
  * `fix_right::Bool = true`: Whether to fix the right endpoint.
  * `damping_constant::Float64`: The damping constant.
  * `initial_condition::Vector{Float64}`: The initial cell positions. Must be sorted.

# Solving

You can solve a `CellProblem` like you would solve a problem from DifferentialEquations.jl, e.g. with 

```
solve(prob, Tsit5(), saveat = 0.1)
```

The other kwargs for `solve` that we provide are:

  * `proliferation::Bool = false`: Whether to include proliferation.
  * `rng::AbstractRNG = Random.default_rng()`: The random number generator to use for proliferation.
  * `sort::Bool = false`: Whether to sort the cells after each step. This is useful for preventing the cells from becoming unsorted, which can happen due to numerical errors or force laws like `F(q) = k/q^(n+1)`, `n ≥ 0`.

For proliferation problems, `EnsembleProblem` can be useful - see the docs.
