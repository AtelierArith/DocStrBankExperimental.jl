```
logdet(m::LinearMixedModel)
```

Return the value of `log(det(Λ'Z'ZΛ + I)) + m.optsum.REML * log(det(LX*LX'))` evaluated in place.

Here LX is the diagonal term corresponding to the fixed-effects in the blocked lower Cholesky factor.
