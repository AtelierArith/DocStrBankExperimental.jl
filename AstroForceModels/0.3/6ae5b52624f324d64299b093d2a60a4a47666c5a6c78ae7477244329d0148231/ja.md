ドラッグアストロモデル構造体は、宇宙船に対するドラッグ力の加速度を計算するための情報を含みます。

# フィールド

  * `satellite_drag_model::AbstractSatelliteDragModel`: 弾道係数を計算するための衛星ドラッグモデル。
  * `atmosphere_model::Symbol`: 密度を計算するための大気モデル。
  * `eop_data::EopIau1980`: 大気モデルを使用して密度を計算するのに役立つ地球の向きパラメータ。
