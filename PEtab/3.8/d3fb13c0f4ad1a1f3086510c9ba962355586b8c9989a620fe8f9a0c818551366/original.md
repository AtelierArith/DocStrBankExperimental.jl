```
to_prior_scale(xpetab, target::PEtabLogDensity)
```

Transforms parameter `x` from the PEtab problem scale to the prior scale.

This conversion is needed for Bayesian inference, as in PEtab.jl Bayesian inference is performed on the prior scale.

!!! note
    To use this function, the Bijectors, LogDensityProblems, and LogDensityProblemsAD packages must be loaded: `using Bijectors, LogDensityProblems, LogDensityProblemsAD`

