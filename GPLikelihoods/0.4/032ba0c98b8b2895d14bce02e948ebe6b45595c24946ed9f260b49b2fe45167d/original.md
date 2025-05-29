```
GammaLikelihood(α::Real=1.0, l=exp)
```

Gamma likelihood with fixed shape `α`.

$$
    p(y|f) = \operatorname{Gamma}(y | α, l(f))
$$

On calling, this returns a Gamma distribution with shape `α` and scale `invlink(f)`.
