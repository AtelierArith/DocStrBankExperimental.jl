```
BNNODE(chain, kernel = HMC; strategy = nothing, draw_samples = 2000,
       priorsNNw = (0.0, 2.0), param = [nothing], l2std = [0.05],
       phystd = [0.05], phynewstd = [0.05], dataset = [nothing], physdt = 1 / 20.0,
       MCMCargs = (; n_leapfrog=30), nchains = 1, init_params = nothing,
       Adaptorkwargs = (; Adaptor = StanHMCAdaptor, targetacceptancerate = 0.8,
                          Metric = DiagEuclideanMetric),
       Integratorkwargs = (Integrator = Leapfrog,), autodiff = false,
       progress = false, verbose = false)
```

Algorithm for solving ordinary differential equations using a Bayesian neural network. This is a specialization of the physics-informed neural network which is used as a solver for a standard `ODEProblem`.

!!! warn
    Note that BNNODE only supports ODEs which are written in the out-of-place form, i.e. `du = f(u,p,t)`, and not `f(du,u,p,t)`. If not declared out-of-place, then the BNNODE will exit with an error.


## Positional Arguments

  * `chain`: A neural network architecture, defined as a `Lux.AbstractLuxLayer`.
  * `kernel`: Choice of MCMC Sampling Algorithm. Defaults to `AdvancedHMC.HMC`

## Keyword Arguments

(refer `NeuralPDE.ahmc_bayesian_pinn_ode` keyword arguments.)

## Example

```julia
linear = (u, p, t) -> -u / p[1] + exp(t / p[2]) * cos(t)
tspan = (0.0, 10.0)
u0 = 0.0
p = [5.0, -5.0]
prob = ODEProblem(linear, u0, tspan, p)
linear_analytic = (u0, p, t) -> exp(-t / 5) * (u0 + sin(t))

sol = solve(prob, Tsit5(); saveat = 0.05)
u = sol.u[1:100]
time = sol.t[1:100]
x̂ = u .+ (u .* 0.2) .* randn(size(u))
dataset = [x̂, time]

chainlux = Lux.Chain(Lux.Dense(1, 6, tanh), Lux.Dense(6, 6, tanh), Lux.Dense(6, 1))

alg = BNNODE(chainlux; draw_samples = 2000, l2std = [0.05], phystd = [0.05],
             priorsNNw = (0.0, 3.0), progress = true)

sol_lux = solve(prob, alg)

# with parameter estimation
alg = BNNODE(chainlux; dataset, draw_samples = 2000, l2std = [0.05], phystd = [0.05],
             priorsNNw = (0.0, 10.0), param = [Normal(6.5, 0.5), Normal(-3, 0.5)],
             progress = true)

sol_lux_pestim = solve(prob, alg)
```

## Solution Notes

Note that the solution is evaluated at fixed time points according to the strategy chosen. ensemble solution is evaluated and given at steps of `saveat`. Dataset should only be provided when ODE parameter Estimation is being done. The neural network is a fully continuous solution so `BPINNsolution` is an accurate interpolation (up to the neural network training result). In addition, the `BPINNstats` is returned as `sol.fullsolution` for further analysis.

## References

Liu Yanga, Xuhui Menga, George Em Karniadakis. "B-PINNs: Bayesian Physics-Informed Neural Networks for Forward and Inverse PDE Problems with Noisy Data".

Kevin Linka, Amelie Schäfer, Xuhui Meng, Zongren Zou, George Em Karniadakis, Ellen Kuhl "Bayesian Physics Informed Neural Networks for real-world nonlinear dynamical systems".
