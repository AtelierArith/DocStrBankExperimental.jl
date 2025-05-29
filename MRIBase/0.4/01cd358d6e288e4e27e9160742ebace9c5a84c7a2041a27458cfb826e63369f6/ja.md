```
multiEchoData(acqData::AcquisitionData, coil::Int64, slice::Int64;rep::Int64=1)
```

は、与えられた `coil`、`slice` および `rep`（繰り返し）に対して、`acqData` に含まれるすべてのエコーの k 空間を返します。
