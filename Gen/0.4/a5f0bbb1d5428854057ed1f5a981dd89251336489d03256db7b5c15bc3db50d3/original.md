```
new_trace = elliptical_slice(
    trace, addr, mu, cov;
    check=false, observations=EmptyChoiceMap())
```

Apply an elliptical slice sampling update to a given random choice with a multivariate normal prior.

Also takes the mean vector and covariance matrix of the prior.

[Reference URL](http://proceedings.mlr.press/v9/murray10a/murray10a.pdf)
