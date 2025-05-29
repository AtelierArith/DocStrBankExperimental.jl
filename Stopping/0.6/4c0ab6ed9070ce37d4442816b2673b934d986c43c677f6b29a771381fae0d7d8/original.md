init_max_counters:  initialize the maximum number of evaluations on each of the functions present in the NLPModels.Counters, e.g.

`init_max_counters(; allevals :: T = typemax(T), obj = allevals, grad = allevals, cons = allevals, jcon = allevals, jgrad = allevals, jac = allevals, jprod = allevals, jtprod = allevals, hess = allevals, hprod = allevals, jhprod = allevals, sum = 11 * allevals, kwargs...)`

`:neval_sum` is by default limited to `|Counters| * allevals`.
