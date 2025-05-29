```
UKFMeasurementModel{inplace_measurement,augmented_measurement}(measurement, R2, ny, ne, innovation, mean, cov, cross_cov, weight_params, cache = nothing)
```

無香カーマンフィルタのための測定モデル。

# 引数:

  * `measurement`: 測定関数 `y = h(x, u, p, t)`
  * `R2`: 測定ノイズ共分散行列
  * `ny`: 測定変数の数
  * `ne`: `augmented_measurement` が `true` の場合、測定ノイズ変数の数
  * `innovation(y::AbstractVector, yh::AbstractVector)` ここで、引数は (測定出力, 予測出力) を表します。
  * `mean(ys::AbstractVector{<:AbstractVector})`: 出力シグマ点のベクトルの平均を計算します。
  * `cov(ys::AbstractVector{<:AbstractVector}, y::AbstractVector)`: 出力シグマ点の共分散行列を計算します。
  * `cross_cov(xs::AbstractVector{<:AbstractVector}, x::AbstractVector, ys::AbstractVector{<:AbstractVector}, y::AbstractVector, W::UKFWeights)` ここで、引数は (状態シグマ点, 平均状態, 出力シグマ点, 平均出力, 重み) を表します。この関数は、状態と出力シグマ点の間の重み付き**クロス共分散**行列を返す必要があります。
  * `weight_params`: 無香変換重みのパラメータを保持する型です。詳細については [`UnscentedKalmanFilter`](@ref) および [Docs: Unscented transform](https://baggepinnen.github.io/LowLevelParticleFilters.jl/dev/ut/) を参照してください。
