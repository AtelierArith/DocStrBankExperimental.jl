```julia
TrackingState(
    system,
    carrier_doppler,
    code_phase;
    code_doppler,
    carrier_phase,
    carrier_loop_filter,
    code_loop_filter,
    sc_bit_detector,
    num_ants,
    correlator,
    integrated_samples,
    prompt_accumulator,
    cn0_estimator
)

```

便利なTrackingStateコンストラクタ。必須パラメータはGNSSシステム、キャリアドップラー`carrier_doppler`、およびコードフェーズ`code_phase`です。オプションのパラメータは

  * コードドップラー`code_doppler`、デフォルトはキャリアドップラーにコード/中心周波数比を掛けたもの
  * キャリアフェーズ`carrier_phase`、デフォルトは0
  * キャリアループフィルター`carrier_loop_filter`、デフォルトは`ThirdOrderBilinarLF()`
  * コードループフィルター`code_loop_filter`、デフォルトは`SecondOrderBilinearLF()`
  * アンテナ要素の数`num_ants`、デフォルトは`NumAnts(1)`
  * 相関器`correlator`、デフォルトは`get_default_correlator(...)`
  * 統合サンプル`integrated_samples`、デフォルトは0
  * ビット検出用のプロンプトアキュムレータ`prompt_accumulator`、デフォルトは0
  * CN0推定器`cn0_estimator`、デフォルトは`MomentsCN0Estimator(20)`
