```
VolData_combined = combine_vol_data(VolData::NamedTuple; lat=nothing, lon=nothing, depth=nothing, dims=(100,100,100), dataset_preferred = 1)
```

This takes different volumetric datasets (specified in `VolData`) & merges them into a single one. You need to either provide the "reference" dataset within the NamedTuple (`dataset_preferred`), or the lat/lon/depth and dimensions of the new dataset.
