```
multiCoilData(acqData::AcquisitionData, echo::Int64, slice::Int64;rep::Int64=1)
```

は、与えられた `echo`、`slice`、および `rep`（繰り返し）に対して、すべてのコイルの `acqData` に含まれる k 空間を返します。
