```
TRARCSolver(nlp::AbstractNLPModel [, x0 = nlp.meta.x0]; kwargs...)
TRARCSolver(stp::NLPStopping; kwargs...)
```

Structure regrouping all the structure used during the `TRARC` call. It returns a `TRARCSolver` structure.

# Arguments

The keyword arguments may include:

  * `stp::NLPStopping`: `Stopping` structure for this algorithm workflow;
  * `meta::ParamData`: see [`ParamData`](@ref);
  * `workspace::TRARCWorkspace`: allocated space for the solver itself;
  * `TR::ARTrustRegion`: trust-region parameters.
