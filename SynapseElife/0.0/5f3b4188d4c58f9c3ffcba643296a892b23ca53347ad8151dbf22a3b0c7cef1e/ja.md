```julia
evolveSynapse(
    xc0,
    xd0,
    p_synapse,
    events_sorted_times,
    is_pre_or_post_event,
    bap_by_epsp,
    is_glu_released,
    algos;
    verbose,
    progress,
    abstol,
    reltol,
    save_positions,
    nu,
    kwargs...
)

```

シナプスモデルのシミュレーションを実行します。その他のことの中で、シナプスに影響を与える外部イベントを提供する必要があります：グルタミン酸の放出とBaP。

# 引数

  * `xc0` 連続変数の初期条件。例 `xc0 = Synapse.initial_conditions_continuous_temp(p_synapse)`
  * `xd0` 離散変数の初期条件。例 `xd0 = Synapse.initial_conditions_discrete(p_synapse)`
  * `p_synapse::SynapseParams` シナプスパラメータ。例 `p_synapse = SynapseParams()`.
  * `events_sorted_times` 外部イベント（グルタミン酸 / BaP）のためのソートされた時間リスト（ms）
  * `is_pre_or_post_event::Vector{Bool}` `events_sorted_times` の対応するイベントがグルタミン酸イベントであるかどうか。`false` の場合、BaPイベントに対応します。
  * `bap_by_epsp::Vector{<:Real}` 追加のBaP時間イベント、これらはEPSPによって引き起こされます。`is_events_glu` にインデックスされたものに追加されます。
  * `is_glu_released::Vector{Bool}` グルタミン酸イベントをシャットダウンするための変数、すなわちグルタミン酸の振幅をゼロにします。この変数は、いくつかの実験を再現するために便利です。`false` の場合、グルタミン酸の振幅はゼロに設定されます。
  * `algos` `PiecewiseDeterministicMarkovProcesses` からのシミュレーションアルゴリズム。例えば `(PDMP.CHV(:lsoda), PDMP.CHV(:lsoda))`

# オプション引数

  * `verbose = false` シミュレーション中に情報を表示
  * `abstol = 1e-8` ODEタイムステッパーの絶対許容誤差
  * `reltol = 1e-7` ODEタイムステッパーの相対許容誤差
  * `progress = false` シミュレーション中にプログレスバーを表示
  * `save_positions = (false, true)` ジャンプ（遷移）の前後の値を保存
  * `nu` 遷移行列。`buildTransitionMatrix()` で初期化されます。
