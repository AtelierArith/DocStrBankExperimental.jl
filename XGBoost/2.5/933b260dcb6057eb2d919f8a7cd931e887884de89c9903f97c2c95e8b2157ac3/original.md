```
importance(b::Booster, type="gain")
```

Compute feature importance metric from a trained [`Booster`](@ref). Valid options for `type` are

  * `"gain"`
  * `"weight"`
  * `"cover"`
  * `"total_gain"`
  * `"total_cover"`

The output is an `OrderedDict` with keys corresponding to feature names and values corresponding to importances.  The importances are always returned as `Vector`s, typically with length 1 but possibly longer in multi-class cases.  If feature names were not set the keys of the output dict will be integers giving the feature column number.  The output will be sorted with the highest importance feature listed first and the lowest importance feature listed last.

See [`importancetable`](@ref) for a way to generate a tabular summary of all available feature importances and [`importancereport`](@ref) for a convenient text display of it.
