```
test_fit_trace_hierarchical(; G, R, S, insertstep, transitions, rtarget, rinit, nsamples, onstates, totaltime, ntrials, fittedparam, propcv, cv, interval, noisepriors, hierarchical, method, maxtime, nchains)
```

Fit a simulated trace dataset using a hierarchical model and compare to the target.

# Arguments

  * `G`, `R`, `S`, `insertstep`, `transitions`: Model structure.
  * `rtarget`, `rinit`: Rate parameters.
  * `nsamples`, `onstates`, `totaltime`, `ntrials`: Data and simulation options.
  * `fittedparam`, `propcv`, `cv`, `interval`, `noisepriors`, `hierarchical`, `method`, `maxtime`, `nchains`: Fitting options.

# Returns

  * Tuple of (median fitted parameters, target parameters).
