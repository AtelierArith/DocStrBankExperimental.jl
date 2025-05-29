```
FFJORD(model, tspan, input_dims, args...; ad = nothing, basedist = nothing, kwargs...)
```

Constructs a continuous-time recurrent neural network, also known as a neural ordinary differential equation (neural ODE), with fast gradient calculation via adjoints [1] and specialized for density estimation based on continuous normalizing flows (CNF) [2] with a stochastic approach [2] for the computation of the trace of the dynamics' jacobian. At a high level this corresponds to the following steps:

1. Parameterize the variable of interest x(t) as a function f(z, θ, t) of a base variable z(t) with known density p_z.
2. Use the transformation of variables formula to predict the density p_x as a function of the density p_z and the trace of the Jacobian of f.
3. Choose the parameter θ to minimize a loss function of p_x (usually the negative likelihood of the data).

After these steps one may use the NN model and the learned θ to predict the density p_x for new values of x.

Arguments:

  * `model`: A `Flux.Chain` or `Lux.AbstractLuxLayer` neural network that defines the dynamics of the model.
  * `basedist`: Distribution of the base variable. Set to the unit normal by default.
  * `input_dims`: Input Dimensions of the model.
  * `tspan`: The timespan to be solved on.
  * `args`: Additional arguments splatted to the ODE solver. See the [Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) documentation for more details.
  * `ad`: The automatic differentiation method to use for the internal jacobian trace. Defaults to `AutoForwardDiff()` if full jacobian needs to be computed, i.e. `monte_carlo = false`. Else we use `AutoZygote()`.
  * `kwargs`: Additional arguments splatted to the ODE solver. See the [Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) documentation for more details.

References:

[1] Pontryagin, Lev Semenovich. Mathematical theory of optimal processes. CRC press, 1987.

[2] Chen, Ricky TQ, Yulia Rubanova, Jesse Bettencourt, and David Duvenaud. "Neural ordinary differential equations." In Proceedings of the 32nd International Conference on Neural Information Processing Systems, pp. 6572-6583. 2018.

[3] Grathwohl, Will, Ricky TQ Chen, Jesse Bettencourt, Ilya Sutskever, and David Duvenaud. "Ffjord: Free-form continuous dynamics for scalable reversible generative models." arXiv preprint arXiv:1810.01367 (2018).
