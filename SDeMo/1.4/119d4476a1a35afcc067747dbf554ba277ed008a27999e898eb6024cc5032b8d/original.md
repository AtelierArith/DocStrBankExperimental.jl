```
VarianceInflationFactor{N}
```

Removes variables one at a time until the largest VIF is lower than `N` (a floating point number), or the performancde of the model stops increasing. Note that the resulting set of variables may have a largest VIF larger than the threshold. See `StrictVarianceInflationFactor` for an alternative.
