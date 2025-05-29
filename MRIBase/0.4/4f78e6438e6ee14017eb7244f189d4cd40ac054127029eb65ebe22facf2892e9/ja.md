```
AcquisitionData(f::RawAcquisitionData; estimateProfileCenter::Bool=false, OffsetBruker=false)
```

は `RawAcquisitionData` を同等の `AcquisitionData` オブジェクトに変換します。OffsetBruker=true の場合、Y/Z方向のみの位置を補正するために位相オフセットを追加します。
