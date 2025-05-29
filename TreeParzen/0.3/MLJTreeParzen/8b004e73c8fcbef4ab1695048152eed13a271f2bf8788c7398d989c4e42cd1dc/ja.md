```julia
MLJTreeParzenTuning(
;
    threshold,
    draws,
    linear_forgetting,
    prior_weight,
    random_trials,
    max_simultaneous_draws
) -> TreeParzen.MLJTreeParzen.MLJTreeParzenTuning

```

キーワード引数コンストラクタ

  * `threshold::Float64`; デフォルト 0.25。これは `TreeParzen.Config.gamma` と同じです。
  * `draws::Int`; デフォルト 24。これは `TreeParzen.Config.draws` と同じです。
  * `linear_forgetting::Int`; デフォルト 25。これは `TreeParzen.Config.linear_forgetting` と同じです。
  * `prior_weight::Float64`; デフォルト 1.0。これは `TreeParzen.Config.prior_weight` と同じです。
  * `random_trials::Int`; デフォルト 20。これは `TreeParzen.Config.random_trials` と同じです。
  * `max_simultaneous_draws::Int`; デフォルト 1。MLJインターフェース特有で、TreeParzen最適化中に履歴更新なしで引き出される候補ハイパーパラメータの数を制御します（提案/ランダムサンプリングのウォームアップ中ではなく）、MLJの並列モデルトレーニングを可能にします。
