```
ROITrace
```

単一のROIトレースの分析結果を表します。

フィールド:

  * `raw_trace`: 生の蛍光トレース
  * `dfof`: ベースライン補正後のΔF/Fトレース
  * `t_series`: トレースの時間点
  * `stim_start_time`: 刺激の開始時間 (s)
  * `stim_end_time`: 刺激の終了時間 (s)
  * `channel`: チャンネルインデックス
  * `stimulus_index`: このトレースに対応する刺激のインデックス
  * `fit_parameters`: 曲線フィッティングからのパラメータ [振幅, tau*on, tau*off, 遅延]
  * `is_significant`: 応答が有意かどうか
