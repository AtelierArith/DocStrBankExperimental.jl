```
convertRawToAcq(rawData::::RawAcquisitionData)
```

生データをMRIReco.jlを使用して取得データに変換し、その後小さな調整を適用します。取得データ構造を返します。

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# 引数

  * `rawData::RawAcquisitionData` - MRIReco.jlを使用して生データを読み込むことで得られた生データ構造
