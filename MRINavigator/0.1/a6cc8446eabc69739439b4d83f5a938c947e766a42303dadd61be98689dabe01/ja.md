```
Data = additionalNavInput(
    noisemat::Array{Complex{Float32}, 2},
    rawData::RawAcquisitionData,
    acqData::AcquisitionData,
    acqMap::Union{AcquisitionData, Nothing} = nothing,
    nav_time::Union{Array{Complex{Float32}, 2}, Nothing} = nothing,
    trace::Union{Matrix{Float64}, Nothing} = nothing,
    centerline::Union{Vector{Float64}, Nothing} = nothing)
```

navCorr!への入力として必要な追加データ構造を構築します！

# 引数

  * `noisemat::Array{Complex{Float32}, 2}` - ExtractNoiseData!で取得したノイズデータ
  * `rawData::RawAcquisitionData` - MRIReco.jlで生データを読み込んで取得した生データ構造
  * `acqData::AcquisitionData` - MRIReco.jlで生データを変換して取得した取得データ構造

# デフォルト値がnothingのオプション引数

  * `acqMap::Union{AcquisitionData, Nothing} = nothing`       - MRIReco.jlで参照データを変換して取得した取得データ構造
  * `nav_time::Union{Array{Complex{Float32}, 2}, Nothing}`    - ExtractNavigatorで取得したナビゲータデータのタイムスタンプ（1日の始まりからのms）
  * `trace::Union{Matrix{Float64}, Nothing}`                  - 呼吸トレースのタイムスタンプと値を持つ2列の行列（1:時間 [ms], 2:トレース）。画像取得の前後の時間点を含める（少なくとも2秒）。
  * `centerline::Union{Vector{Float64}, Nothing}`             - callSCTで取得した脊髄中心線の座標

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
