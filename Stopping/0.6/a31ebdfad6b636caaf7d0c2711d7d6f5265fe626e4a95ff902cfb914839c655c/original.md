init_max_counters_NLS:  initialize the maximum number of evaluations on each of the functions present in the `NLPModels.NLSCounters`, e.g.

`init_max_counters_NLS(; allevals = typemax(T), residual = allevals, jac_residual = allevals, jprod_residual = allevals, jtprod_residual = allevals, hess_residual = allevals, jhess_residual = allevals, hprod_residual = allevals, kwargs...)`
