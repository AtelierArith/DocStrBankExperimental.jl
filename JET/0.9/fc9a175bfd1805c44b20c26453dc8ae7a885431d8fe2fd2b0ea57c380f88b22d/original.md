```
reportkey(report::InferenceErrorReport)
```

Returns an identifier for the runtime-dispatched call site of `report`.

If you have a long list of reports to analyze, `urpts = unique(reportkey, rpts)` may remove "duplicates" that arrive at the same runtime dispatch from different entry points.
