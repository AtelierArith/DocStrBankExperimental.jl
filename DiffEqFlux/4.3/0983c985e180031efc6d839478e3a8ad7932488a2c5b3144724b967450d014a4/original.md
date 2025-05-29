```
NeuralODEMM(model, constraints_model, tspan, mass_matrix, alg = nothing, args...;
    sensealg = InterpolatingAdjoint(autojacvec = ZygoteVJP()), kwargs...)
```

Constructs a physically-constrained continuous-time recurrant neural network, also known as a neural differential-algebraic equation (neural DAE), with a mass matrix and a fast gradient calculation via adjoints [1]. The mass matrix formulation is:

$$
Mu' = f(u,p,t)
$$

where `M` is semi-explicit, i.e. singular with zeros for rows corresponding to the constraint equations.

Arguments:

  * `model`: A `Flux.Chain` or `Lux.AbstractLuxLayer` neural network that defines the ̇`f(u,p,t)`
  * `constraints_model`: A function `constraints_model(u,p,t)` for the fixed constraints to impose on the algebraic equations.
  * `tspan`: The timespan to be solved on.
  * `mass_matrix`: The mass matrix associated with the DAE.
  * `alg`: The algorithm used to solve the ODE. Defaults to `nothing`, i.e. the default algorithm from DifferentialEquations.jl. This method requires an implicit ODE solver compatible with singular mass matrices. Consult the [DAE solvers](https://docs.sciml.ai/DiffEqDocs/stable/solvers/dae_solve/) documentation for more details.
  * `sensealg`: The choice of differentiation algorithm used in the backpropogation. Defaults to an adjoint method. See the [Local Sensitivity Analysis](https://docs.sciml.ai/SciMLSensitivity/stable/) documentation for more details.
  * `kwargs`: Additional arguments splatted to the ODE solver. See the [Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) documentation for more details.
