```
Jstat(m::AbstractGMMResult)
```

Return the Hansen's J statistic for over-identified GMM. `NaN` is returned for one-step GMM or the case where parameters are just-identified.
