```
BayesianLinearRegressor{Tmw, TΛw}
```

A Bayesian Linear Regressor is a distribution over linear functions given by

```julia
w ~ Normal(mw, Λw)
f(x) = dot(x, w)
```

where `mw` and `Λw` are the mean and precision of `w`, respectively.
