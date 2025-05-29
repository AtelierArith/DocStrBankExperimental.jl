PEtabLogDensity(prob::PEtabODEProblem)

Create a `LogDensityProblem` using the posterior and gradient functions from `prob`.

This [`LogDensityProblem` interface](https://github.com/tpapp/LogDensityProblems.jl) defines everything needed to perform Bayesian inference with packages such as `AdvancedHMC.jl` (which includes algorithms like NUTS, used by `Turing.jl`), and `AdaptiveMCMC.jl`.
