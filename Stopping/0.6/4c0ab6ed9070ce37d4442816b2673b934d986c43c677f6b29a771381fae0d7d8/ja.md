init*max*counters: 各NLPModels.Countersに存在する関数の最大評価数を初期化します。例えば、

`init_max_counters(; allevals :: T = typemax(T), obj = allevals, grad = allevals, cons = allevals, jcon = allevals, jgrad = allevals, jac = allevals, jprod = allevals, jtprod = allevals, hess = allevals, hprod = allevals, jhprod = allevals, sum = 11 * allevals, kwargs...)`

`:neval_sum`はデフォルトで`|Counters| * allevals`に制限されています。
