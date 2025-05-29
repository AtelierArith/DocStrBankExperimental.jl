```
ADLChargeDriftModel{T <: SSDFloat, M <: AbstractDriftMaterial, N, TM <: AbstractTemperatureModel{T}} <: AbstractChargeDriftModel{T}
```

AGATA検出器ライブラリに基づく電子とホールのための電荷ドリフトモデル。計算の詳細な説明は[ADL Charge Drift Model](@ref)を参照してください。

## フィールド

  * `electrons::CarrierParameters{T}`: <100>および<111>軸に沿った電子ドリフトを記述するためのパラメータ。
  * `holes::CarrierParameters{T}`: <100>および<111>軸に沿ったホールドリフトを記述するためのパラメータ。
  * `crystal_orientation::SMatrix{3,3,T,9}`: グローバル座標系を結晶の<100>、<010>、<001>軸によって与えられる結晶座標系に変換する回転行列。
  * `γ::SVector{N,SMatrix{3,3,T,9}}`: 導電帯の`N`バレーに対する逆質量テンソル。
  * `parameters::ADLParameters{T}`: 電子ドリフト速度の計算に必要なパラメータ。
  * `temperaturemodel::TM`: 温度に対する結果のドリフト速度をスケールするモデル。

さらに[`CarrierParameters`](@ref)も参照してください。
