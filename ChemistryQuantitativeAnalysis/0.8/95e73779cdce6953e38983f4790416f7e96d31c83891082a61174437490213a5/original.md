```
inv_predict(cal::AbstractCalibration, dt::AbstractDataTable; analyte = first(cal.analyte))
inv_predict(cal::SingleCalibration, y::AbstractArray)
inv_predict(cal::MultipleCalibration, y::AbstractArray)
inv_predict(cal::SingleCalibration)
inv_predict(cal::MultipleCalibration)
```

Inversely predict concentration of `analyte` or analyte specified in `cal`, and return the result as a vector using data in `dt`, `y` or `cal.table.y` as inverse predictors.
