```
navOutput = NavCorr!(nav::Array{Complex{T}, 4}, acqData::AcquisitionData, params::Dict{Symbol, Any}, addData::additionalNavInput) where {T}
```

ナビゲーターに基づく補正を計算し、取得データに適用します。利用可能な複数のパイプラインがあります: "knav", "FFT" および "FFT*unwrap"。ナビゲーターのトレース、再構成された画像座標における脊髄中心線、各スライスおよび位置におけるナビゲーターとベルトデータの相関、各スライスのラップされたポイントの位置を返します。params辞書のcorr*typeフィールドを使用してパイプラインを選択してください。

# 引数

  * `nav::Array{Complex{T}, 4}` - ExtractNavigator関数で取得したナビゲータープロファイル
  * `acqData::AcquisitionData` - MRIReco.jlを使用して生データを変換して得られた取得データ構造
  * `params::Dict{Symbol, Any}` - ナビゲーター補正パラメータの辞書
  * `addData::additionalNavInput` - コンストラクタ: additionalNavInputで取得した必須の追加データ構造

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
