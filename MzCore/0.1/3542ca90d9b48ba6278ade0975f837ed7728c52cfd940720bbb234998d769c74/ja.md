```
axmz, axtime = limits(scans)
```

スキャンシーケンスの制限を、`Axis{:mz}` と `Axis{:time}` として返します。`Axis` は `AxisArrays` からのものです。`axtime` は時間単位（`Unitful` から）を持つべきですが、`axmz` は無次元です。制限は（`IntervalSets` から）区間として表現されるべきです。
