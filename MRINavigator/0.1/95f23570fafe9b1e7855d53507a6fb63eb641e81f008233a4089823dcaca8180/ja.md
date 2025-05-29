```
CopyTE!(rawData::RawAcquisitionData, acqData::AcquisitionData)
```

MRIReco.jlの生データ構造から取得データ構造にTE値をコピーします。

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# 引数

  * `rawData::RawAcquisitionData` - MRIReco.jlを使用して生データを読み込むことで得られる生データ構造
  * `acqData::AcquisitionData` - MRIReco.jlを使用して生データを変換することで得られる取得データ構造
