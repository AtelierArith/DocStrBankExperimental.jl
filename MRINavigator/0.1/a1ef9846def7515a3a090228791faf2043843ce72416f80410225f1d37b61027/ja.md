```
img = directreco(acq::AcquisitionData)
```

MRIReco.jl再構成関数を呼び出し、再構成された画像を返します。コイルを別々に再構成します。

# 引数

  * `acqData::RawAcquisitionData` - MRIReco.jlを使用して生データを変換して得られた取得データ構造

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
