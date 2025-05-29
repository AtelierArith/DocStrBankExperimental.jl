```
Refit(DM::AbstractDataModel, startp::AbstractVector=MLE(DM); kwargs...)
```

Refits `DM` via `InformationGeometry.minimize` and returns result as new `DataModel`.
