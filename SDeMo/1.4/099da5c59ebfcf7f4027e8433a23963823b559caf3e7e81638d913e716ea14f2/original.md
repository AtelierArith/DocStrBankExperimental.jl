```
StrictVarianceInflationFactor{N}
```

Removes variables one at a time until the largest VIF is lower than `N` (a floating point number). By contrast with `VarianceInflationFactor`, this approach to variable selection will *not* cross-validate the model, and might result in a model that is far worse than any other variable selection technique.
