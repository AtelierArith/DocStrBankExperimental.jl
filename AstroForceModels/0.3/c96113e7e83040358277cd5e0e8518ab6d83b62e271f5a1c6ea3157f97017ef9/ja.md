```
compute_density(JD::Number, u::AbstractArray, eop_data::EopIau1980, AtmosphereType::AtmosphericModelType)
```

指定された日時、位置、eop_data、および大気タイプに基づいて、ある点での大気密度を計算します。

# 引数

  * `JD::Number`: ユリウス日でのシミュレーションの現在の時間。
  * `u::AbstractArray`: シミュレーションの現在の状態。
  * `eop_data::EopIau1980`: 地球の姿勢パラメータ。
  * `AtmosphereType::AtmosphericModelType`: 密度を計算するために使用される大気モデルのタイプ。利用可能なオプションは、Jacchia-Bowman 2008 (JB2008)、Jacchia-Roberts 1971 (JR1971)、NRL MSIS 2000 (MSIS2000)、指数関数的 (ExpAtmo)、およびなし (None) です。

# 戻り値

  * `rho::Number`: 指定された時間と地点での大気の密度 [kg/m^3]。
