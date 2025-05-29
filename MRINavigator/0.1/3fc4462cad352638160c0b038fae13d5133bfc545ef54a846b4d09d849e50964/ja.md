```
sensit = CompSensit(acq::AcquisitionData, thresh = 0.13)
```

脊髄イメージングに調整されたマスキングを使用してコイルの感度マップを計算します。MRIReco.jlのMRICoilSensitivities.jlを代わりに使用してください。

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# 引数

  * `acqData::RawAcquisitionData` - MRIReco.jlを使用して生データを変換して得られた取得データ構造
  * `tresh::Float64` - マスキングしきい値: マスクサイズを縮小するために増加させ、マスクサイズを拡大するために減少させます
