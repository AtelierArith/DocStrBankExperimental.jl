```
cgf(d::UnivariateDistribution, t)
```

Evaluate the [cumulant-generating function](https://en.wikipedia.org/wiki/Cumulant) of distribution `d` at `t`.

The cumulant-generating-function is the logarithm of the [moment-generating function](https://en.wikipedia.org/wiki/Moment-generating_function): `cgf = log ∘ mgf`. In practice, however, the right hand side may have overflow issues.

See also [`mgf`](@ref)
