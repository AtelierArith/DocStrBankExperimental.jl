```
compute_scans!(dataset::UVDataSet, minΔt::Number=-1)
```

与えられた時系列と最小スキャン間隔からスキャンIDを特定します。特定されたスキャンIDの整数配列を返します。

  * dataset::DimStack
  * `minΔt`: スキャン間の最小間隔（秒単位）。
