```
test_fit_trace(; G, R, S, insertstep, transitions, rtarget, rinit, nsamples, onstates, totaltime, ntrials, fittedparam, propcv, cv, interval, noisepriors, nchains)
```

Fit a simulated trace dataset using the provided parameters and compare to the target.

# Arguments

  * `G`, `R`, `S`, `insertstep`, `transitions`: Model structure.
  * `rtarget`, `rinit`: Rate parameters.
  * `nsamples`, `onstates`, `totaltime`, `ntrials`: Data and simulation options.
  * `fittedparam`, `propcv`, `cv`, `interval`, `noisepriors`, `nchains`: Fitting options.

# Returns

  * Tuple of (fitted rates, target rates).
