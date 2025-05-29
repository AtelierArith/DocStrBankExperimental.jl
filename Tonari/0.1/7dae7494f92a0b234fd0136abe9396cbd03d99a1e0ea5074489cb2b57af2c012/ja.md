```
Simulation(model::Model, T::Real, Δt::Real, S_high::Real, S_low::Real, t::AbstractVector{Real})
```

確率過程のシミュレーションに関する情報を含む構造体です。

# フィールド

  * `model::Model`: プロセスのパワースペクトル密度。
  * `T::Real`: シミュレーションされた時系列の期間。タイムスタンプは0から`T`までであるため、期間は`T`です。
  * `Δt::Real`: サンプリング期間、またはサンプル間の最小時間差。
  * `S_high::Real`: シミュレーションのために最大周波数を乗算する係数。
  * `S_low::Real`: シミュレーションのために最小周波数を除算する係数。
  * `t::AbstractVector{Real}`: 時間ベクトル。この場合、プロセスがサンプリングされる時間です。時間ベクトルはソートされていると仮定されています。

# コンストラクタ

  * `Simulation(model::Model, T::Real, Δt::Real, S_high::Real, S_low::Real, t::AbstractVector{Real})`: 定期的なサンプリングでシミュレーションを構築します。
  * `Simulation(model::Model, T::Real, Δt::Real)`: 定期的なサンプリングでシミュレーションを構築し、`S_high`と`S_low`を10.0に設定します。
  * `Simulation(model::Model, T::Real, Δt::Real, S_high::Real, S_low::Real)`: 指定されたパラメータでシミュレーションを構築します。
  * `Simulation(model::Model, t::AbstractVector{Real}, S_high::Real, S_low::Real)`: `t`によって与えられたサンプリングパターンでシミュレーションを構築します。
  * `Simulation(model::Model, t::AbstractVector{Real})`: `t`によって与えられたサンプリングパターンでシミュレーションを構築し、`S_high`と`S_low`を10.0に設定します。
