```
test_fit_tracejoint(; coupling, G, R, S, insertstep, transitions, rtarget, rinit, nsamples, onstates, totaltime, ntrials, fittedparam, propcv, cv, interval, noisepriors, maxtime, method)
```

Fit a simulated joint trace dataset for coupled models and compare to the target.

# Arguments

  * `coupling`, `G`, `R`, `S`, `insertstep`, `transitions`: Model structure and coupling.
  * `rtarget`, `rinit`: Rate parameters.
  * `nsamples`, `onstates`, `totaltime`, `ntrials`: Data and simulation options.
  * `fittedparam`, `propcv`, `cv`, `interval`, `noisepriors`, `maxtime`, `method`: Fitting options.

# Returns

  * Tuple of (fitted rates, target rates).
