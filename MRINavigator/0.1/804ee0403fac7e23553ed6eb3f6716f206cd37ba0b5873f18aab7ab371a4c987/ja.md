```
apply_corr!(nav::Array{T, 4}, acqd::AcquisitionData, numechoes::Int64, numlines::Int64, numsamples::Int64, numslices::Int64) where {T}
```

ナビゲーターに基づく補正を、MRIReco.jlを使用して生データを読み込むことで得られた取得データ構造に適用します。補正を適用した後、画像は再構成されるべきです。reconstruct関数を使用してください。

# 引数

  * `nav::Array{T, 4}` - ナビゲータデータから得られた位相推定
  * `acqd::AcquisitionData` - MRIReco.jlを使用して生データを変換することで得られた取得データ構造
  * `numechoes::Int64` - エコーの数
  * `numlines::Int64` - 各スライスおよびエコーの行（プロファイル）の数
  * `numsamples::Int64` - 各プロファイルのサンプル数
  * `numslices::Int64` - スライスの数

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
