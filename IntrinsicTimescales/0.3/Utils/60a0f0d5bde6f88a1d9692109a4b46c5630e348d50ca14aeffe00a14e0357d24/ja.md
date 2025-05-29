```
lorentzian_initial_guess(psd, freqs; min_freq=freqs[1], max_freq=freqs[end])
```

ローレンツィアンフィッティングの初期パラメータを推定します。

# 引数

  * `psd::AbstractVector{<:Real}`: パワースペクトル密度値
  * `freqs::AbstractVector{<:Real}`: 周波数値
  * `min_freq::Real`: 考慮する最小周波数
  * `max_freq::Real`: 考慮する最大周波数

# 戻り値

  * Vector{Float64}: [振幅, ニー周波数] の初期推定

# 注意事項

  * 低周波数の平均パワーから振幅を推定します。
  * 半パワーポイントからニー周波数を推定します。
  * allow*variable*exponent=true の場合、指数の初期推定を 2.0 に設定します。
  * 非線形フィッティングの出発点として使用されます。
