```
AnalysisCallback(semi; interval=0,
                       extra_analysis_errors=Symbol[],
                       extra_analysis_integrals=(),
                       io=stdout)
```

Analyze a numerical solution every `interval` time steps. The L2- and the L∞-norm for each component are computed by default. Additional errors can be computed, e.g. by passing `extra_analysis_errors = (:conservation_error,)`.

Further scalar functions `func` in `extra_analysis_integrals` are applied to the numerical solution and integrated over the computational domain. Some examples for this are [`entropy`](@ref), and [`energy_total`](@ref). You can also write your own function with the same signature as the examples listed above and pass it via `extra_analysis_integrals`. The computed errors and intergrals are saved for each timestep and can be obtained by calling [`errors`](@ref) and [`integrals`](@ref).

During the Simulation, the `AnalysisCallback` will print information to `io`.
