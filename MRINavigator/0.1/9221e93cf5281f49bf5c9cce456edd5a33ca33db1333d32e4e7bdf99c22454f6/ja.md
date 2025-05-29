```
AdjustSubsampleIndices!(acqData::AcquisitionData)
```

MRIReco.jlの取得データ構造にサブサンプルインデックスを追加します。最初の繰り返しで取得されていないデータを変換する際に必要です。

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# 引数

  * `acqData::AcquisitionData` - MRIReco.jlを使用して生データを変換して得られた取得データ構造
