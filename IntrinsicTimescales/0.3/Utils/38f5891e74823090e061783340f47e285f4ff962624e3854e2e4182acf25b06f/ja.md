```
find_knee_frequency(psd, freqs; dims=ndims(psd), min_freq=freqs[1], max_freq=freqs[end])
```

ローレンツィアンをフィッティングしてパワースペクトル密度から膝周波数を見つけます。

# 引数

  * `psd::AbstractArray{T}`: パワースペクトル密度の値
  * `freqs::Vector{T}`: 周波数の値
  * `dims::Int=ndims(psd)`: 計算を行う次元
  * `min_freq::T=freqs[1]`: 考慮する最小周波数
  * `max_freq::T=freqs[end]`: 考慮する最大周波数
  * `constrained::Bool=false`: 制約付き最適化を使用するかどうか
  * `allow_variable_exponent::Bool=false`: 可変指数を許可するかどうか（PLE）

# 戻り値

  * 方程式 amp/(1 + (f/knee)^{exponent}）のフィットのベクトル。

allow*variable*exponent=false の場合、指数=2を仮定し、[振幅, 膝*周波数]を返します。true の場合、[振幅, 膝*周波数, 指数]を返します。

# 注意事項

  * NonlinearSolve.jlを使用したローレンツィアンフィッティング
  * 振幅の初期推定は低周波パワーの平均値に基づいています。膝については、これは半パワーポイントです。指数については、2.0です。
