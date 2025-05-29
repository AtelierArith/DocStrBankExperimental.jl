```
multiCoilMultiEchoData(acqData::AcquisitionData, echo::Int64, slice::Int64;rep::Int64=1)
```

は、与えられた `slice` と `rep`（繰り返し）に対して、すべてのコイル、エコーの k 空間を `acqData` から返します。
