```
mask = CompRoughMask(acq::AcquisitionData, slices::Int64, thresh)
```

複数のスライスに対して、均一でない可能性のある粗いマスクを返します。

# 引数

  * `acqData::RawAcquisitionData` - 生データをMRIReco.jlで変換して得られた取得データ構造
  * `slices::Int64` - 取得データのスライス数
  * `tresh::Float64` - マスキング閾値：マスクサイズを縮小するには増加させ、マスクサイズを拡大するには減少させます

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
