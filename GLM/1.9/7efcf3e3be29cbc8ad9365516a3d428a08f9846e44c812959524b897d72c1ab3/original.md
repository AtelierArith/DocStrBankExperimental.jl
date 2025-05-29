```
dispersion(m::AbstractGLM, sqr::Bool=false)
```

Return the estimated dispersion (or scale) parameter for a model's distribution, generally written σ for linear models and ϕ for generalized linear models. It is, by definition, equal to 1 for the Bernoulli, Binomial, and Poisson families.

If `sqr` is `true`, the squared dispersion parameter is returned.
