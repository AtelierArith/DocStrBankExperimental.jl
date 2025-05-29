```julia
stp(
    t_end,
    param,
    all_events_times,
    is_pre_or_post_index;
    _plot,
    nu_stp,
    kwargs...
)

```

この関数は、前シナプス側のシミュレーションを実行します。

# 引数:

  * `t_end` シミュレーション時間の終了
  * `param` パラメータを含む名前付きタプル、例: `(τ_rec = 20000, δ_decay = .0004, tau_pre = 20, tau_soma = 40)`
  * `all_events_times` 外部イベントの時間のソートされたリスト
  * `is_pre_or_post_index` 外部イベントが前 (`true`) か後 (`false`) か

# キーワード引数

  * `_plot = false` 結果をプロットするかどうか
  * `nu_stp = stp_build_transition_matrix()` 遷移行列

# 出力

  * `is_glu_release` `true` (成功) または `false` (失敗)、小胞（グルタミン酸）の放出を引き起こした `all_events_index` の前シナプス刺激のリスト
  * `D`、また (XD[2,:])、ドッキングプールの進化
  * `R`、また (XD[3,:])、予備プールの進化
  * `time` シミュレーション時間
  * `glu_release_times` 成功した放出（グルタミン酸）が発生した時間のベクトル
  * `bap_by_epsp_times` EPSPによってAPが引き起こされた時間のベクトル
