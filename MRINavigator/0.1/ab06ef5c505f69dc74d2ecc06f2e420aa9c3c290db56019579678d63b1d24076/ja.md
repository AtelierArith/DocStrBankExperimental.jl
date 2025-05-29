```
CompResizeSaveSensit(acqMap::AcquisitionData, acqData::AcquisitionData, path_sensit::String)
```

画像データの次元にリサイズし、脊髄イメージングに調整されたマスキングでコイル感度マップを保存します。代わりにMRIReco.jlのMRICoilSensitivities.jlを使用してください。

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# 引数

  * `acqMap::RawAcquisitionData` - MRIReco.jlを使用して生データを変換して得られた取得データ構造
  * `acqData::RawAcquisitionData` - MRIReco.jlを使用して生データを変換して得られた取得データ構造
  * `tresh::Float64` - マスキング閾値: マスクサイズを縮小するには増加させ、マスクサイズを拡張するには減少させます

```
