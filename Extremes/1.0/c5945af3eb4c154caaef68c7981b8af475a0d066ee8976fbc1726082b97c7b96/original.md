```
returnlevel(fm::pwmAbstractExtremeValueModel{BlockMaxima, T} where T<:Distribution, returnPeriod::Real)::ReturnLevel
```

Compute the confidence intervel for the return level corresponding to the return period `returnPeriod` from the fitted model `fm` with confidence level `confidencelevel`.
