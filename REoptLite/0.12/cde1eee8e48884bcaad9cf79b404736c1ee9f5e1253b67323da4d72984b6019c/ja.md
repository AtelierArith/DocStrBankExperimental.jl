```
simulate_outages(d::Dict, p::REoptInputs; microgrid_only::Bool=false)
```

年の各時間ステップで開始する停電の時系列シミュレーション。これは、各停電で重要な負荷が満たされる時間ステップの数を計算するために使用され、これにより重要な負荷を満たす確率を決定します。

# 引数

  * `d`::Dict `reopt_results`からの辞書
  * `p`::REoptInputs `reopt_results`から辞書を生成した入力
  * `microgrid_only`::Bool 最適なマイクログリッド容量のみをシミュレートするか、総容量をシミュレートするか。この入力は、複数の停電をモデル化する際にのみ関連します。

辞書を返します

```julia
{
    "resilience_by_timestep": 各時間ステップで開始する停電に対して重要な負荷が満たされる時間ステップのベクトル,
    "resilience_hours_min": "resilience_by_timestep"の最小値,
    "resilience_hours_max": "resilience_by_timestep"の最大値,
    "resilience_hours_avg": "resilience_by_timestep"の平均値,
    "outage_durations": 生存の確率がゼロでない停電の持続時間に対する整数のベクトル,
    "probs_of_surviving": "outage_durations"に対応する確率のベクトル,
    "probs_of_surviving_by_month": 月単位で計算された確率のベクトル,
    "probs_of_surviving_by_hour_of_the_day": 時間単位で計算された確率のベクトル,
}
```
