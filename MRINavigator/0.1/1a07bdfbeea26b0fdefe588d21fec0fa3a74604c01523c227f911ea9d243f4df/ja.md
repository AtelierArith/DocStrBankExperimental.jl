```
SelectSlice!(acqd, nav, nav_time, idx_slice)
```

取得データ構造から1つ以上のエコーを抽出します

# 引数

  * `acqd::AcquisitionData` - MRIReco.jlを使用して生データを変換して得られた取得データ構造
  * `idx_slice::Vector{Int64}` - 選択するスライスのインデックスを含むベクター（0から始まる、下のスライス）

# デフォルト値がnothingのオプション引数

  * `nav::Union{Array{Complex{T}, 4}, Nothing} = nothing` - ExtractNavigator関数で得られたナビゲータプロファイル
  * `nav_time::Union{Array{Complex{Float32}, 2}, Nothing}` - ExtractNavigatorで得られたナビゲータデータのタイムスタンプ（1日の始まりからのミリ秒）

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
