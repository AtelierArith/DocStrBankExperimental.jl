```
img = Reconstruct(acqd::AcquisitionData, sensit::Array{Complex{T},4}, noisemat::Union{Array{Complex{T}},Nothing} = nothing)
```

MRIReco.jl再構成関数を呼び出し、再構成された画像を返します。入力は単一の繰り返しのみです。

# 引数

  * `acqData::RawAcquisitionData` - MRIReco.jlを使用して生データを変換して得られた取得データ構造
  * `sensit::Array{Complex{T},4}` - CompSensit(acq::AcquisitionData, thresh = 0.135)を使用して計算されたコイル感度マップ行列
  * `noisemat::Union{Array{Complex{T}},Nothing} = nothing` - ExtractNoiseData!(rawData::RawAcquisitionData)を使用して生データ構造から抽出されたノイズデータ

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
