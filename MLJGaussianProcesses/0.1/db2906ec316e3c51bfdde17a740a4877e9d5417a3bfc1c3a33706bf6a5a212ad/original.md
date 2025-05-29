```
GPR
```

A model type for constructing a gpr, based on [MLJGaussianProcesses.jl](https://github.com/john-waczak/MLJGaussianProcesses.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
GPR = @load GPR pkg=MLJGaussianProcesses
```

Do `model = GPR()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `GPR(μ=...)`. MLJGaussianProcesses implements [Gaussian Process Regression](https://gaussianprocess.org/gpml/chapters/RW2.pdf), a non-parametric, non-linear regression model for supervised machine learning utilizing tools from the [JuliaGaussianProcesses](https://juliagaussianprocesses.github.io/) organization.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with     mach = machine(model, X, y) where

  * `X`: an `AbstractMatrix` or `Table` of input features whose columns are of scitype `Continuous.`

Train the machine with `fit!(mach, rows=...)`.

  * `y`: a `Vector` of target variables of scitype `Continuous`.

# Hyper-parameters

  * `μ=0`: Constant value to use for mean function of Gaussian Process.
  * `k=default_kernel`: A function `k(θ)` which takes parameters `θ` and returns a `KernelFunction`. `default_kernel` is the classic RBF kernel with variance `σf²`, and length scale `ℓ`
  * `θ_init=θ_default`: Default parameters to initialize the optimization. Defaults to `θ_default = (1.0, 1.0)` for the default kernel.
  * `σ²=1e-6`: Measurement noise (variance). Must be greater than `0` to ensure stability of internal Cholesky factorization.
  * `optimizer:LBFGS()`: Optimizer from `Optim.jl`.

# Operations

  * `predict(mach, X)`:  Returns a vector of normal distributions for each predicted target.
  * `predict_mean(mach, X)`: Return a vector of means from the distribution of predicted targets.
  * `predict_mode(mach, X)`: Return a vector of modes from the distribution of predicted targets.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `θ_best`: A named tuple of best parameters found during GPR fit.
  * `σ²`: The best fit for the measurement variance.

# Report

The fields of `report(mach)` are:

  * `summary`: A summary of results of the optimization.
  * `minimizer`: The parameters that minimized the marginal log-likelihood for the GPR model.
  * `minimum`: The minimum value of minus the marginal log-likelihood during optimization.
  * `iterations`: The number of steps taken by the optimizer
  * `converged`: Whether or not the optimization scheme converged in the allotted number of iterations.

# Examples

```
using MLJ
gpr = @load GPR pkg=MLJGaussianProcesses
model = gpr()
X, y = make_regression(50, 3) # synthetic data
mach = machine(model, X, y) |> fit!
p_y = predict(mach, X)
ŷ = predict_mean(mach, X)
rpt = report(mach)
```
