```
spacemean(A::ClimArray [, W]) = spaceagg(mean, A, W)
```

Average `A` over its spatial coordinates. Optionally provide statistical weights in `W`.
