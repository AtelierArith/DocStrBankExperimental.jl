```
quantification(cal::AbstractCalibration, dt::AbstractDataTable; analyte = cal.analyte)
```

`dt`のデータを信号として使用して`analyte`を定量化し、結果をベクトルとして返します。
