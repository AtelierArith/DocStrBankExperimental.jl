```
did_resample::Bool = maybe_resample!(state::ParticleFilterState;
    ess_threshold::Float64=length(state.traces)/2, verbose=false)
```

Do a resampling step if the effective sample size is below the given threshold. Return `true` if a resample thus occurred, `false` otherwise.
