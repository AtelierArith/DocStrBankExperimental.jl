```julia
defaultFixedLagOnTree!(dfg; ...)
defaultFixedLagOnTree!(dfg, len; limitfixeddown)

```

Enable defaults for fixed-lag-like operation by using smart message passing on the tree.

Notes:

  * These are only default settings, and can be modified in each use case scenario.
  * Default does not update downsolve through to leaves of the tree.
