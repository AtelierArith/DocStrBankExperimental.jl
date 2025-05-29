censored_loglikelihood(X::UnivariateDistribution, t, δ)

分布 X の点 t における検閲された対数尤度を、状態指標 δ を用いて提供します。これは次のように定義されます。

$$
δ * loghazard(X,t) - cumhazard(X,t)
$$
