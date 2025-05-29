```
ahmc_bayesian_pinn_ode(prob, chain; strategy = GridTraining, dataset = [nothing],
                       init_params = nothing, draw_samples = 1000, physdt = 1 / 20.0f0,
                       l2std = [0.05], phystd = [0.05], phynewstd = [0.05], priorsNNw = (0.0, 2.0),
                       param = [], nchains = 1, autodiff = false, Kernel = HMC,
                       Adaptorkwargs = (Adaptor = StanHMCAdaptor,
                           Metric = DiagEuclideanMetric, targetacceptancerate = 0.8),
                       Integratorkwargs = (Integrator = Leapfrog,),
                       MCMCkwargs = (n_leapfrog = 30,), progress = false,
                       verbose = false)
```

!!! warn
    Note that `ahmc_bayesian_pinn_ode()` only supports ODEs which are written in the out-of-place form, i.e. `du = f(u,p,t)`, and not `f(du,u,p,t)`. If not declared out-of-place, then `ahmc_bayesian_pinn_ode()` will exit with an error.


## Example

```julia
linear = (u, p, t) -> -u / p[1] + exp(t / p[2]) * cos(t)
tspan = (0.0, 10.0)
u0 = 0.0
p = [5.0, -5.0]
prob = ODEProblem(linear, u0, tspan, p)

### CREATE DATASET (Necessity for accurate Parameter estimation)
sol = solve(prob, Tsit5(); saveat = 0.05)
u = sol.u[1:100]
time = sol.t[1:100]

### dataset and BPINN create
x̂ = collect(Float64, Array(u) + 0.05 * randn(size(u)))
dataset = [x̂, time]

chain1 = Lux.Chain(Lux.Dense(1, 5, tanh), Lux.Dense(5, 5, tanh), Lux.Dense(5, 1)

### simply solving ode here hence better to not pass dataset(uses ode params specified in prob)
fh_mcmc_chain1, fhsamples1, fhstats1 = ahmc_bayesian_pinn_ode(prob, chain1,
                                                            dataset = dataset,
                                                            draw_samples = 1500,
                                                            l2std = [0.05],
                                                            phystd = [0.05],
                                                            priorsNNw = (0.0,3.0))

### solving ode + estimating parameters hence dataset needed to optimize parameters upon + Pior Distributions for ODE params
fh_mcmc_chain2, fhsamples2, fhstats2 = ahmc_bayesian_pinn_ode(prob, chain1,
                                                            dataset = dataset,
                                                            draw_samples = 1500,
                                                            l2std = [0.05],
                                                            phystd = [0.05],
                                                            priorsNNw = (0.0,3.0),
                                                            param = [Normal(6.5,0.5), Normal(-3,0.5)])
```

## NOTES

Dataset is required for accurate Parameter estimation + solving equations Incase you are only solving the Equations for solution, do not provide dataset

## Positional Arguments

  * `prob`: DEProblem(out of place and the function signature should be f(u,p,t).
  * `chain`: Lux Neural Netork which would be made the Bayesian PINN.

## Keyword Arguments

  * `strategy`: The training strategy used to choose the points for the evaluations. By default GridTraining is used with given physdt discretization.
  * `init_params`: initial parameter values for BPINN (ideally for multiple chains different initializations preferred)
  * `nchains`: number of chains you want to sample
  * `draw_samples`: number of samples to be drawn in the MCMC algorithms (warmup samples are ~2/3 of draw samples)
  * `l2std`: standard deviation of BPINN prediction against L2 losses/Dataset
  * `phystd`: standard deviation of BPINN prediction against Chosen Underlying ODE System
  * `phynewstd`: standard deviation of new loss func term
  * `priorsNNw`: Tuple of (mean, std) for BPINN Network parameters. Weights and Biases of BPINN are Normal Distributions by default.
  * `param`: Vector of chosen ODE parameters Distributions in case of Inverse problems.
  * `autodiff`: Boolean Value for choice of Derivative Backend(default is numerical)
  * `physdt`: Timestep for approximating ODE in it's Time domain. (1/20.0 by default)
  * `Kernel`: Choice of MCMC Sampling Algorithm (AdvancedHMC.jl implementations HMC/NUTS/HMCDA)
  * `Integratorkwargs`: `Integrator`, `jitter_rate`, `tempering_rate`. Refer: https://turinglang.org/AdvancedHMC.jl/stable/
  * `Adaptorkwargs`: `Adaptor`, `Metric`, `targetacceptancerate`. Refer: https://turinglang.org/AdvancedHMC.jl/stable/ Note: Target percentage (in decimal) of iterations in which the proposals are accepted (0.8 by default)
  * `MCMCargs`: A NamedTuple containing all the chosen MCMC kernel's (HMC/NUTS/HMCDA) Arguments, as follows :

      * `n_leapfrog`: number of leapfrog steps for HMC
      * `δ`: target acceptance probability for NUTS and HMCDA
      * `λ`: target trajectory length for HMCDA
      * `max_depth`: Maximum doubling tree depth (NUTS)
      * `Δ_max`: Maximum divergence during doubling tree (NUTS)

    Refer: https://turinglang.org/AdvancedHMC.jl/stable/
  * `progress`: controls whether to show the progress meter or not.
  * `verbose`: controls the verbosity. (Sample call args in AHMC)

!!! warning
    AdvancedHMC.jl is still developing convenience structs so might need changes on new releases.

