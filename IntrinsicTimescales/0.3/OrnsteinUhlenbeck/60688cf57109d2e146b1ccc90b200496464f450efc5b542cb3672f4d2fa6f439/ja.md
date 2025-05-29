```
generate_ou_with_oscillation(theta, dt, duration, num_trials, data_mean, data_var)
```

加法振動を伴う1次元OUプロセスを生成します。

# 引数

  * `theta::Vector{T}`: パラメータ [タイムスケール, 周波数, 係数]
  * `dt::Real`: 時間ステップサイズ
  * `duration::Real`: 総時間長
  * `num_trials::Integer`: 試行回数
  * `data_mean::Real`: 目標平均値
  * `data_var::Real`: 目標分散

# 戻り値

  * Matrix{Float64}: 次元が (num*trials, num*timesteps) の生成データ

# 注意事項

  * 係数は0と1の間に制限されています
  * OUプロセスと正弦波振動を組み合わせています
  * 出力を標準化し、目標の平均と分散に合わせてスケーリングします
  * SciMLソルバーが失敗した場合はNaN行列を返します
