```
Refit(DM::AbstractDataModel, startp::AbstractVector=MLE(DM); kwargs...)
```

`DM`を`InformationGeometry.minimize`を介して再フィットし、結果を新しい`DataModel`として返します。
