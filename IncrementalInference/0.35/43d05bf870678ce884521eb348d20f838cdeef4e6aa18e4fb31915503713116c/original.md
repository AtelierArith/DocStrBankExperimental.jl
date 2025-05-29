```julia
doautoinit!(dfg, xi; solveKey, singles, N, logger)

```

EXPERIMENTAL: initialize target variable `xi` based on connected factors in the factor graph `fgl`.  Possibly called from `addFactor!`, or `doCliqAutoInitUp!` (?).

Notes:

  * Special carve out for multihypo cases, see issue 427.

Development Notes:

  * Target factor is first (singletons) or second (dim 2 pairwise) variable vertex in `xi`.
  * TODO use DFG properly with local operations and DB update at end.
  * TODO get faster version of `isInitialized` for database version.
  * TODO: Persist this back if we want to here.
  * TODO: init from just partials
