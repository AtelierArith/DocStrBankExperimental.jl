```
compute_scans!(dataset::UVDataSet, minΔt::Number=-1)
```

Identify Scan IDs from a given time series and minimum scan seperation. Returns an integer array for the identified scan IDs.

  * dataset::DimStack
  * `minΔt`: minimum seperation between the scans in seconds.
