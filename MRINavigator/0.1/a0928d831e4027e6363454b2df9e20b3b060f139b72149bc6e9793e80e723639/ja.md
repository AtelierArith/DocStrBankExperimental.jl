```
nav = TE_corr!(nav::Array{T, 4}, acqd::AcquisitionData, dt_nav::Float64, TE_nav::Float64, numsamples::Int64, numechoes::Int64) where {T}
```

ナビゲーター補正の位相値を、各データサンプルの正確な取得時間と各エコーに基づいて計算します。四次元のナビゲーター配列を返します。

# 引数

  * `nav::Array{T, 4}` - ナビゲーターデータから得られた位相推定値
  * `acqData::AcquisitionData` - MRIReco.jlを使用して生データを変換して得られた取得データ構造
  * `dt_nav::Float64` - 周波数エンコーディング方向の2つのサンプル間の時間間隔
  * `TE_nav::Float64` - ナビゲーター読み出しのエコー時間
  * `numsamples::Int64` - 各プロファイルのサンプル数
  * `numechoes::Int64` - エコーの数

MRIReco 参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
