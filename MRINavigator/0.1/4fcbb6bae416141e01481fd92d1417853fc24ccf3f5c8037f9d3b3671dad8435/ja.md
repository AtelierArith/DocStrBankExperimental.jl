```
flags = ExtractFlags(rawData::RawAcquisitionData)
```

MRIReco.jlの生データプロファイルから取得フラグを抽出します。各プロファイルに対して31要素のベクトルを返します。

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# 引数

  * `rawData::RawAcquisitionData` - MRIReco.jlを使用して生データを読み込むことで得られる生データ構造
