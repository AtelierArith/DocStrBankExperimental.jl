```julia
factorCanInitFromOtherVars(dfg, fct, loovar; solveKey)

```

Return `(::Bool, ::OKVarlist, ::NotOkayVarList)` on whether all other variables (besides `loovar::Symbol`) attached to factor `fct::Symbol` are all initialized – i.e. `fct` is usable.

Notes:

  * Special carve out for multihypo cases, see issue 427, where at least one hypothesis should be available, but not all required at first.

Development Notes

  * TODO get faster version of isInitialized for database version

Related

doautoinit!, initVariable!, isInitialized, isMultihypo
