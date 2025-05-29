```
sensit = ResizeSensit!(sensit::Array{Complex{T},4}, acqMap::AcquisitionData, acqData::AcquisitionData)
```

コイル感度マップを取得データの視野と解像度に合わせてリサイズおよびリサンプリングします。このステップは画像再構成を実行するために必要です。画像データと参照データは同じスライス中心を持っている必要があります。

# 引数

  * `sensit::Array{Complex{T},4}` - CompSensit(acq::AcquisitionData, thresh) の出力
  * `acqMap::RawAcquisitionData` - MRIReco.jlを使用して生の参照データを変換して得られた取得データ構造
  * `acqData::RawAcquisitionData` - MRIReco.jlを使用して生データを変換して得られた取得データ構造

MRIReco 参照: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
