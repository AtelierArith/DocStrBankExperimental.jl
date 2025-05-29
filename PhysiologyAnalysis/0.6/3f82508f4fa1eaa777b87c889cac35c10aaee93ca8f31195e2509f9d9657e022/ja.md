```
process_rois(data::Experiment{TWO_PHOTON, T}; 
    stim_indices=nothing,
    channels=nothing,
    roi_indices=nothing,
    delay_time=50.0,
    window::Int=15,
    n_stds=2.0,
    sig_window=50.0,  # 刺激後の有意な反応を探すための時間ウィンドウ（ms）
    analysis_window_before=100.0,  # 刺激前に分析するための時間ウィンドウ（ms）
    analysis_window_after=50.0,   # 刺激後に分析するための時間ウィンドウ（ms）
    kwargs...
) where T<:Real
```

二光子イメージングデータから関心領域（ROI）を処理する手順は以下の通りです：

1. ピクセルをROIに分割します（まだ行われていない場合はpixel*splits*roi!を使用）
2. 各ROIおよびチャネルについて：

      * ROIトレースを抽出
      * 刺激前の期間を使用してベースラインを計算
      * 移動平均補正を使用してdF/Fを計算
      * 反応にパラメトリックモデルをフィット
      * 指定された時間ウィンドウ内のしきい値に基づいて有意性を計算

返り値：     各ROIの処理されたデータを含むROIAnalysisオブジェクト
