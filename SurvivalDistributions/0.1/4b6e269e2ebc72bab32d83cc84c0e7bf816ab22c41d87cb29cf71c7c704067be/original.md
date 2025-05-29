censored_loglikelihood(X::UnivariateDistribution, t, δ)

Provide the censored logliklyhood of the distribution X at point t, with status indicatrix δ. Is if defined as 

$$
δ * loghazard(X,t) - cumhazard(X,t)
$$
