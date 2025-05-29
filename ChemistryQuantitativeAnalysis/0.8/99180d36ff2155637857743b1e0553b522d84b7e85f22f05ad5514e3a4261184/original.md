```
quantification(cal::AbstractCalibration, dt::AbstractDataTable; analyte = cal.analyte)
```

Quantify `analyte` using data in `dt` as signals, and return the result as a vector.
