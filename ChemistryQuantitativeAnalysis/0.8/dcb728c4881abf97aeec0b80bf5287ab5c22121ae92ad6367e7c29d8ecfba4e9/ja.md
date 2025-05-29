```
accuracy(at::AnalysisTable; true_conc = :true_concentration, est_conc = :estimated_concentration) 
accuracy(dtp::AbstractDataTable, dtt::AbstractDataTable)
accuracy(cal::MultipleCalibration, tbl = cal.table)
accuracy(cal::SingleCalibration, tbl)
accuracy(x̂::AbstractVector, x::AbstractVector)
```

精度を計算し、値を `AbstractDataTable` または `Vector` として返します。 `tbl` は `cal.table` と同様に、`y` と `x` の2つのプロパティを含む必要があります。
