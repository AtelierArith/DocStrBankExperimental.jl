Creates an `OptimizationProblem` for use in [`Optimization.jl`](https://docs.sciml.ai/Optimization/stable/) to find the optimal parameters.

# Arguments:

  * `ψ`: material model to use
  * `test` or `tests`: A single or vector of hyperelastics tests to use when fitting the parameters
  * `u₀`: Initial guess for parameters
  * `ps`: Any additional parameters for calling predict
  * `adb`: Select differentiation type from [`ADTypes.jl`](https://github.com/SciML/ADTypes.jl). The type is automatically applied to the type of AD applied to the Optimization Problem also.
  * `loss`: Loss function from [`LossFunctions.jl`](https://github.com/JuliaML/LossFunctions.jl)
