```
test_fit_rna(; gene, G, nalleles, propcv, fittedparam, fixedeffects, transitions, rinit, datacond, datapath, label, root, nchains)
```

Fit a real RNA histogram using the provided parameters and compare to the data.

# Arguments

  * `gene`, `G`, `nalleles`: Gene and model structure.
  * `propcv`, `fittedparam`, `fixedeffects`, `transitions`, `rinit`: Fitting options.
  * `datacond`, `datapath`, `label`, `root`: Data and file options.
  * `nchains`: Number of MCMC chains.

# Returns

  * Tuple of (predicted histogram, normalized data histogram).
