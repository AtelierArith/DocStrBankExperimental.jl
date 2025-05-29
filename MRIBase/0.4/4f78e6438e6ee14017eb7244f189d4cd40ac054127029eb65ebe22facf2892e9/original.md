```
AcquisitionData(f::RawAcquisitionData; estimateProfileCenter::Bool=false, OffsetBruker=false)
```

converts `RawAcquisitionData` into the equivalent `AcquisitionData` object. If OffsetBruker=true, add a phase offset to correct position only along Y/Z direction
