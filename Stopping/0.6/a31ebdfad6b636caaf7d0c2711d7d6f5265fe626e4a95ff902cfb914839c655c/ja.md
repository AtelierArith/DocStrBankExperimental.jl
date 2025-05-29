`init_max_counters_NLS`: `NLPModels.NLSCounters`に存在する各関数の最大評価回数を初期化します。例えば、

`init_max_counters_NLS(; allevals = typemax(T), residual = allevals, jac_residual = allevals, jprod_residual = allevals, jtprod_residual = allevals, hess_residual = allevals, jhess_residual = allevals, hprod_residual = allevals, kwargs...)`
