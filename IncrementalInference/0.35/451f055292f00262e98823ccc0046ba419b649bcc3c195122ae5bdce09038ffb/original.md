```julia
approxCliqMarginalUp!(csmc; ...)
approxCliqMarginalUp!(
    csmc,
    childmsgs;
    N,
    dbg,
    multiproc,
    logger,
    iters,
    drawpdf
)

```

Approximate Chapman-Kolmogorov transit integral and return separator marginals as messages to pass up the Bayes (Junction) tree, along with additional clique operation values for debugging.

Notes

  * `onduplicate=true` by default internally uses deepcopy of factor graph and Bayes tree, and does **not** update the given objects.  Set false to update `fgl` and `treel` during compute.

Future

  * TODO: internal function chain is too long and needs to be refactored for maintainability.
