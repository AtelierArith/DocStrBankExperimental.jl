```
TruncateStd(nσ::Number)
```

A constraint indicating that the distribution furnishing an uncertain value should be truncated at the mean ± `nσ` (`n` standard deviations).

## Notes

  * Beware when you apply the `TruncateStd` constraint to a (usually a numeric)   population with a small value range. With `nσ` small, you might end up with    a population mean *between* the actual values, so that the range    `[mean(pop) - nσ*std(pop), mean(pop) + nσ*std(pop)]` returns `nothing`.
