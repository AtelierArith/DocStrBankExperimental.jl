```
test_compare(; r, transitions, G, R, S, insertstep, nRNA, nalleles, bins, total, tol, onstates, dttype)
```

Compare simulated and chemical master equation histograms for a given parameter set.

# Arguments

  * `r`: Rate parameters.
  * `transitions`, `G`, `R`, `S`, `insertstep`: Model structure.
  * `nRNA`, `nalleles`: RNA and allele counts.
  * `bins`: Histogram bins.
  * `total`: Number of simulation steps.
  * `tol`: Simulation tolerance.
  * `onstates`, `dttype`: State and dwell time types.

# Returns

  * Tuple of (chemical master histogram, array of simulated histograms).
