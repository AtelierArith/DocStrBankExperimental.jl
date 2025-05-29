```
exact_whittle_est(x::Array; m::Real=0.8, l=0, detrend = true)
```

時系列 `x` の長期記憶パラメータを正確なウィトル対数尤度関数を使用して推定します。詳細については [Shimotsu and Phillips (2005)](https://doi.org/10.1214/009053605000000309) を参照してください。

# 引数

  * `x::Vector`: 時系列
  * `m∈(0,1)::Float64`: テーパーの最終値
  * `l∈(0,1)::Float64`: テーパーの初期値
  * `detrend::Bool`: true の場合、推定前に時系列の平均が除去されます。

# 出力

  * `d::Float64`: 長期記憶パラメータ

# 注意事項

この関数は、時系列 `x` の周期グラムを周波数の区間 `[T^l,T^m]` に対して考慮します。ゼロ周波数は常に除外されます。条件 `m < l` が成り立つ必要があります。`m` と `l` のデフォルト値はそれぞれ 0.8 と 0 です。

# 例

```julia-repl
julia> exact_whittle_est(randn(100,1))
```
