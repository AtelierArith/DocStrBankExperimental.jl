```
ahmc_bayesian_pinn_pde(pde_system, discretization;
    draw_samples = 1000, bcstd = [0.01], l2std = [0.05], phystd = [0.05],
    phynewstd = [0.05], priorsNNw = (0.0, 2.0), param = [], nchains = 1,
    Kernel = HMC(0.1, 30), Adaptorkwargs = (Adaptor = StanHMCAdaptor,
        Metric = DiagEuclideanMetric, targetacceptancerate = 0.8),
    Integratorkwargs = (Integrator = Leapfrog,), saveats = [1 / 10.0],
    numensemble = floor(Int, draw_samples / 3), progress = false, verbose = false)
```

## NOTES

  * Dataset is required for accurate Parameter estimation + solving equations.
  * Returned solution is a BPINNsolution consisting of Ensemble solution, estimated PDE and NN parameters for chosen `saveats` grid spacing and last n = `numensemble` samples in Chain. the complete set of samples in the MCMC chain is returned as `fullsolution`,  refer `BPINNsolution` for more details.

## Positional Arguments

  * `pde_system`: ModelingToolkit defined PDE equation or system of equations.
  * `discretization`: BayesianPINN discretization for the given pde_system, Neural Network and training strategy.

## Keyword Arguments

  * `draw_samples`: number of samples to be drawn in the MCMC algorithms (warmup samples are ~2/3 of draw samples)
  * `bcstd`: Vector of standard deviations of BPINN prediction against Initial/Boundary Condition equations.
  * `l2std`: Vector of standard deviations of BPINN prediction against L2 losses/Dataset for each dependant variable of interest.
  * `phystd`: Vector of standard deviations of BPINN prediction against Chosen Underlying PDE equations.
  * `phynewstd`: Vector of standard deviations of new loss term.
  * `priorsNNw`: Tuple of (mean, std) for BPINN Network parameters. Weights and Biases of BPINN are Normal Distributions by default.
  * `param`: Vector of chosen PDE's parameter's Distributions in case of Inverse problems.
  * `nchains`: number of chains you want to sample.
  * `Kernel`: Choice of MCMC Sampling Algorithm object HMC/NUTS/HMCDA (AdvancedHMC.jl implementations).
  * `Adaptorkwargs`: `Adaptor`, `Metric`, `targetacceptancerate`. Refer: https://turinglang.org/AdvancedHMC.jl/stable/. Note: Target percentage(in decimal) of iterations in which the proposals are accepted (0.8 by default).
  * `Integratorkwargs`: `Integrator`, `jitter_rate`, `tempering_rate`. Refer: https://turinglang.org/AdvancedHMC.jl/stable/
  * `saveats`: Grid spacing for each independent variable for evaluation of ensemble solution, estimated parameters.
  * `numensemble`: Number of last samples to take for creation of ensemble solution, estimated parameters.
  * `progress`: controls whether to show the progress meter or not.
  * `verbose`: controls the verbosity. (Sample call args in AHMC).

!!! warning
    AdvancedHMC.jl is still developing convenience structs so might need changes on new releases.

