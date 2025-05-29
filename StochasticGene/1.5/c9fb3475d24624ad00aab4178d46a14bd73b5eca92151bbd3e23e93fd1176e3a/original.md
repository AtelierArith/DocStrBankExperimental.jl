```
test_fit_rnadwelltime(; rtarget, transitions, G, R, S, insertstep, nRNA, nsamples, nalleles, onstates, bins, dttype, fittedparam, propcv, priorcv, splicetype, maxtime, nchains)
```

Fit a simulated RNA dwell time histogram using the provided parameters and compare to the data.

# Arguments

  * `rtarget`, `transitions`, `G`, `R`, `S`, `insertstep`: Model structure and rates.
  * `nRNA`, `nsamples`, `nalleles`, `onstates`, `bins`, `dttype`: Data and simulation options.
  * `fittedparam`, `propcv`, `priorcv`, `splicetype`, `maxtime`, `nchains`: Fitting options.

# Returns

  * Tuple of (predicted histogram, data PDF).
