```
struct TimeDifferential
    recGeom
```

Differential operator of order `K` to be applied along the time dimension. Applies the ilter `w^k` where `k` is the order. For example, the tinme derivative is `TimeDifferential{1}` and the time integration is `TimeDifferential{-1}`

# Constructor

```
judiTimeIntegration(recGeom, order)
judiTimeIntegration(judiVector, order)

judiTimeDerivative(recGeom, order)
judiTimeDerivative(judiVector, order)
```
