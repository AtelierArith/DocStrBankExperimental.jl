```
test_fit_tracejoint_hierarchical(; coupling, G, R, S, insertstep, transitions, rtarget, rinit, hierarchical, method, nsamples, onstates, totaltime, ntrials, fittedparam, propcv, cv, interval, noisepriors, maxtime, decayrate)
```

Fit a simulated joint trace dataset for coupled models using a hierarchical model and compare to the target.

# Arguments

  * `coupling`, `G`, `R`, `S`, `insertstep`, `transitions`: Model structure and coupling.
  * `rtarget`, `rinit`: Rate parameters.
  * `hierarchical`, `method`: Hierarchical model and method options.
  * `nsamples`, `onstates`, `totaltime`, `ntrials`: Data and simulation options.
  * `fittedparam`, `propcv`, `cv`, `interval`, `noisepriors`, `maxtime`, `decayrate`: Fitting options.

# Returns

  * Tuple of (fitted rates, target rates, fits, stats, measures, model, data, options).
