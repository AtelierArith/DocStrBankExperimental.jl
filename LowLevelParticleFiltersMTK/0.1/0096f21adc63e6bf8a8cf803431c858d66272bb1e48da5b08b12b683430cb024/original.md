```
StateEstimationProblem(model, inputs, outputs; disturbance_inputs, discretization, Ts, df, dg, x0map=[], pmap=[])
```

A structure representing a state-estimation problem.

## Arguments:

  * `model`: An MTK ODESystem model, this model must not have undergone structural simplification.
  * `inputs`: The inputs to the dynamical system, a vector of symbolic variables that must be of type `@variables`.
  * `outputs`: The outputs of the dynamical system, a vector of symbolic variables that must be of type `@variables`.
  * `disturbance_inputs`: The disturbance inputs to the dynamical system, a vector of symbolic variables that must be of type `@variables`. These disturbance inputs indicate where dynamics noise $w$ enters the system. The probability distribution $d_f$ is defined over these variables.
  * `discretization`: A function `discretization(f_cont, Ts, ndiff, nalg, nu) = f_disc` that takes a continuous-tiem dynamics function `f_cont(x,u,p,t)` and returns a discrete-time dynamics function `f_disc(x,u,p,t)`. `ndiff` is the number of differential state variables, `nalg` is the number of algebraic variables, and `nu` is the number of inputs.
  * `Ts`: The discretization time step.
  * `df`: The probability distribution of the dynamics noise $w$. When using Kalman-type estimators, this must be a `MvNormal` or `SimpleMvNormal` distribution.
  * `dg`: The probability distribution of the measurement noise $e$. When using Kalman-type estimators, this must be a `MvNormal` or `SimpleMvNormal` distribution.
  * `x0map`: A dictionary mapping symbolic variables to their initial values. If a variable is not provided, it is assumed to be initialized to zero. The value can be a scalar number, in which case the covariance of the initial state is set to `σ0^2*I(nx)`, and the value can be a `Distributions.Normal`, in which case the provided distributions are used as the distribution of the initial state. When passing distributions, all state variables must be provided values.
  * `σ0`: The standard deviation of the initial state. This is used when `x0map` is not provided or when the values in `x0map` are scalars.
  * `pmap`: A dictionary mapping symbolic variables to their values. If a variable is not provided, it is assumed to be initialized to zero.

## Usage:

Pseudocode

```julia
prob      = StateEstimationProblem(...)
kf        = get_filter(prob, ExtendedKalmanFilter)      # or UnscentedKalmanFilter
filtersol = forward_trajectory(kf, u, y)
sol       = StateEstimationSolution(filtersol, prob)   # Package into higher-level solution object
plot(sol, idxs=[prob.state; prob.outputs; prob.inputs]) # Plot the solution
```
