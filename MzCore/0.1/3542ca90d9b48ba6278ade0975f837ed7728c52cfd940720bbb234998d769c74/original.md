```
axmz, axtime = limits(scans)
```

Return the scan-sequence limits, as an `Axis{:mz}` and `Axis{:time}`. `Axis` is from `AxisArrays`. `axtime` should have time units (from `Unitful`), whereas `axmz` is dimensionless. The limits should be expressed as intervals (from `IntervalSets`).
