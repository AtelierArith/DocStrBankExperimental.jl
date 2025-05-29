```
SingleCalibration{A, N} <: AbstractCalibration{A, N}
```

単一ポイントキャリブレーションのためのすべてのデータを保持する可変型。

# フィールド

  * `analyte`: `Tuple{A}` は既知の濃度を持つ分析物（内部標準）。
  * `conc`: `Float64`、分析物の濃度。
