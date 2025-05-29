```julia
track(
    signal,
    state,
    prn,
    sampling_frequency;
    post_corr_filter,
    intermediate_frequency,
    max_integration_time,
    min_integration_time,
    correlator_sample_shifts,
    early_late_index_shift,
    carrier_loop_filter_bandwidth,
    code_loop_filter_bandwidth,
    velocity_aiding
)

```

信号 `signal` を現在のトラッキング `state`、サンプリング周波数 `sampling_frequency` および PRN `prn` に基づいて追跡します。オプションの設定は次のとおりです：

  * ポスト相関フィルター `post_corr_filter` は `get_default_post_corr_filter(...)` にデフォルト設定されています
  * 中間周波数 `intermediate_frequency` は 0Hz にデフォルト設定されています
  * 最大統合時間 `max_integration_time` は 1ms にデフォルト設定されています。実際の統合時間は、二次コードやビットシフトを見つけるために短くなる場合があります。一度これが見つかると、統合時間は最大統合時間と同じになります。
  * 最小統合時間 `min_integration_time` は 0.75ms にデフォルト設定されています。これは、有効な相関結果をもたらす最小統合時間です。これは最初の統合期間にのみ使用されます。
  * 相関器レプリカのサンプルシフト `correlator_sample_shifts` は `get_correlator_sample_shifts(...)` にデフォルト設定されています
  * キャリアループの帯域幅 `carrier_loop_filter_bandwidth` は 18Hz にデフォルト設定されています
  * コードループの帯域幅 `code_loop_filter_bandwidth` は 1Hz にデフォルト設定されています
  * 速度支援 `velocity_aiding` は 0Hz にデフォルト設定されています
