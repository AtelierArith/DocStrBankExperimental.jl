```
get_significant_roi_pixels(analysis::ROIAnalysis, data::Experiment{TWO_PHOTON}; channel_idx::Int=1)
```

元の画像におけるすべての有意ROIのピクセル座標を取得します。

パラメータ:

  * `analysis`: 処理されたROIデータを含むROIAnalysisオブジェクト
  * `data`: ROIマスクを含む元のExperimentオブジェクト
  * `channel_idx`: 有意ROIを決定するために使用するチャネルインデックス（デフォルト: 1）

戻り値:

  * 指定されたチャネルからの有意ROI内のピクセルの線形インデックスのベクター
