```
NNODE(chain, opt, init_params = nothing; autodiff = false, batch = 0,
      additional_loss = nothing, kwargs...)
```

Algorithm for solving ordinary differential equations using a neural network. This is a specialization of the physics-informed neural network which is used as a solver for a standard `ODEProblem`.

!!! warning
    Note that NNODE only supports ODEs which are written in the out-of-place form, i.e. `du = f(u,p,t)`, and not `f(du,u,p,t)`. If not declared out-of-place, then the NNODE will exit with an error.


## Positional Arguments

  * `chain`: A neural network architecture, defined as a `Lux.AbstractLuxLayer` or          `Flux.Chain`. `Flux.Chain` will be converted to `Lux` using          `adapt(FromFluxAdaptor(), chain)`.
  * `opt`: The optimizer to train the neural network.
  * `init_params`: The initial parameter of the neural network. By default, this is `nothing`                which thus uses the random initialization provided by the neural network                library.

## Keyword Arguments

  * `additional_loss`: A function additional_loss(phi, θ) where phi are the neural network                    trial solutions, θ are the weights of the neural network(s).
  * `autodiff`: The switch between automatic and numerical differentiation for             the PDE operators. The reverse mode of the loss function is always             automatic differentiation (via Zygote), this is only for the derivative             in the loss function (the derivative with respect to time).
  * `batch`: The batch size for the loss computation. Defaults to `true`, means the neural          network is applied at a row vector of values `t` simultaneously, i.e. it's the          batch size for the neural network evaluations. This requires a neural network          compatible with batched data. `false` means which means the application of the          neural network is done at individual time points one at a time. This is not          applicable to `QuadratureTraining` where `batch` is passed in the `strategy`          which is the number of points it can parallelly compute the integrand.
  * `param_estim`: Boolean to indicate whether parameters of the differential equations are                learnt along with parameters of the neural network.
  * `strategy`: The training strategy used to choose the points for the evaluations.             Default of `nothing` means that `QuadratureTraining` with QuadGK is used if no             `dt` is given, and `GridTraining` is used with `dt` if given.
  * `kwargs`: Extra keyword arguments are splatted to the Optimization.jl `solve` call.

## Examples

```julia
u0 = [1.0, 1.0]
ts = [t for t in 1:100]
(u_, t_) = (analytical_func(ts), ts)
function additional_loss(phi, θ)
    return sum(sum(abs2, [phi(t, θ) for t in t_] .- u_)) / length(u_)
end
alg = NNODE(chain, opt, additional_loss = additional_loss)
```

```julia
f(u,p,t) = cos(2pi*t)
tspan = (0.0, 1.0)
u0 = 0.0
prob = ODEProblem(linear, u0 ,tspan)
chain = Lux.Chain(Lux.Dense(1, 5, Lux.σ), Lux.Dense(5, 1))
opt = OptimizationOptimisers.Adam(0.1)
sol = solve(prob, NNODE(chain, opt), verbose = true, abstol = 1e-10, maxiters = 200)
```

## Solution Notes

Note that the solution is evaluated at fixed time points according to standard output handlers such as `saveat` and `dt`. However, the neural network is a fully continuous solution so `sol(t)` is an accurate interpolation (up to the neural network training result). In addition, the `OptimizationSolution` is returned as `sol.k` for further analysis.

## References

Lagaris, Isaac E., Aristidis Likas, and Dimitrios I. Fotiadis. "Artificial neural networks for solving ordinary and partial differential equations." IEEE Transactions on Neural Networks 9, no. 5 (1998): 987-1000.
