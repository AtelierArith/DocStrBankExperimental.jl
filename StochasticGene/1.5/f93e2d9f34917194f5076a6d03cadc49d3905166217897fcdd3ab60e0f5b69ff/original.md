```
test_fit_simrna(; rtarget, transitions, G, nRNA, nalleles, fittedparam, fixedeffects, rinit, totalsteps, nchains)
```

Fit a simulated RNA histogram using the provided parameters and compare to the target.

# Arguments

  * `rtarget`: Target rate parameters.
  * `transitions`, `G`, `nRNA`, `nalleles`: Model structure and counts.
  * `fittedparam`, `fixedeffects`, `rinit`: Fitting options.
  * `totalsteps`: Number of simulation steps.
  * `nchains`: Number of MCMC chains.

# Returns

  * Tuple of (fitted rates, target rates).
