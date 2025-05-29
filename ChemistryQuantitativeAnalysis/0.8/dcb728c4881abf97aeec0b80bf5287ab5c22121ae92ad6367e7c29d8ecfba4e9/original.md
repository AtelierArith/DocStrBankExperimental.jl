```
accuracy(at::AnalysisTable; true_conc = :true_concentration, est_conc = :estimated_concentration) 
accuracy(dtp::AbstractDataTable, dtt::AbstractDataTable)
accuracy(cal::MultipleCalibration, tbl = cal.table)
accuracy(cal::SingleCalibration, tbl)
accuracy(x̂::AbstractVector, x::AbstractVector)
```

Calculate accuracy and return the values as `AbstractDataTable` or `Vector`. `tbl` must contain two properties, `y` and `x`, as same as `cal.table`.
