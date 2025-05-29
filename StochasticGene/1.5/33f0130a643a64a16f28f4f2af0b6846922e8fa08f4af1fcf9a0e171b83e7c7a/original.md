```
test_fit_rnaonoff(; G, R, S, transitions, insertstep, rtarget, rinit, nsamples, nhist, nalleles, onstates, bins, fittedparam, propcv, priorcv, splicetype, nchains)
```

Fit a simulated RNA on-off histogram using the provided parameters and compare to the data.

# Arguments

  * `G`, `R`, `S`, `transitions`, `insertstep`: Model structure.
  * `rtarget`, `rinit`: Rate parameters.
  * `nsamples`, `nhist`, `nalleles`, `onstates`, `bins`: Data and simulation options.
  * `fittedparam`, `propcv`, `priorcv`, `splicetype`, `nchains`: Fitting options.

# Returns

  * Tuple of (predicted histogram, data PDF).
