```
SysState{P}
```

基本的なシステム状態。これらのうちの1つが各タイムステップごとに保存されます。Pはテザー粒子の数です。

  * `time::Float64`: シミュレーション開始からの時間 [s]
  * `t_sim::Float64`: 1つのシミュレーションタイムステップに必要な時間 [s]
  * `sys_state::Int16`: システム状態制御の状態
  * `cycle::Int16`: サイクル番号
  * `fig_8::Int16`: 現在のサイクルの8の字の番号
  * `e_mech::Float64`: 機械エネルギー [Wh]
  * `orient::StaticArraysCore.MVector{4, Float32}`: カイトの向き（クォータニオン、順序 w,x,y,z）
  * `turn_rates::StaticArraysCore.MVector{3, Float32}`: ボディ固定のx, y, z軸周りの旋回速度 [rad/s]
  * `elevation::Float32`: 高度角 [rad]
  * `azimuth::Float32`: 風参照フレームにおける方位角 [rad]
  * `l_tether::StaticArraysCore.MVector{4, Float32}`: テザーの長さ、テザー1から4 [m]
  * `v_reelout::StaticArraysCore.MVector{4, Float32}`: リールアウト速度、テザー1から4 [m/s]
  * `force::StaticArraysCore.MVector{4, Float32}`: テザーの力、テザー1から4 [N]
  * `depower::Float32`: デパワー設定 [0..1]
  * `steering::Float32`: 実際の操舵 [-1..1]
  * `kcu_steering::Float32`: kcu後の操舵、オフセットとデパワースケーリングを適用する前 [-1..1]
  * `set_steering::Float32`: 操舵の設定値 [-1..1]
  * `heading::Float32`: 進行方向角 [rad]
  * `heading_rate::Float32`: 進行方向速度 [rad/s]
  * `course::Float32`: コース角 [rad]
  * `bearing::Float32`: ベアリング角（進行方向/コースの設定値） [rad]
  * `attractor::StaticArraysCore.MVector{2, Float32}`: アトラクター座標（方位角、高度角） [rad]
  * `v_app::Float32`: 見かけの風速のノルム [m/s]
  * `v_wind_gnd::StaticArraysCore.MVector{3, Float32}`: 基準高さでの風ベクトル [m/s]
  * `v_wind_200m::StaticArraysCore.MVector{3, Float32}`: 200mの高さでの風ベクトル [m/s]
  * `v_wind_kite::StaticArraysCore.MVector{3, Float32}`: カイトの高さでの風ベクトル [m/s]
  * `AoA::Float32`: 攻撃角 [rad]
  * `side_slip::Float32`: サイドスリップ角 [rad]
  * `alpha3::Float32`: 粒子Cでの攻撃角 [rad]
  * `alpha4::Float32`: 粒子Dでの攻撃角 [rad]
  * `CL2::Float32`: 揚力係数
  * `CD2::Float32`: 抵抗係数
  * `aero_force_b::StaticArraysCore.MVector{3, Float32}`: KB参照フレームにおける空力力 [N]
  * `aero_moment_b::StaticArraysCore.MVector{3, Float32}`: KB参照フレームにおける空力モーメント [Nm]
  * `twist_angles::StaticArraysCore.MVector{4, Float32}`: 4つのセグメントグループのツイスト角 [rad]
  * `vel_kite::StaticArraysCore.MVector{3, Float32}`: カイトの速度ベクトル [m/s]
  * `acc::Float32`: 加速度 [m/s²]
  * `X::StaticArraysCore.MVector{P, Float32} where P`: x方向の粒子位置のベクトル [m]
  * `Y::StaticArraysCore.MVector{P, Float32} where P`: y方向の粒子位置のベクトル [m]
  * `Z::StaticArraysCore.MVector{P, Float32} where P`: z方向の粒子位置のベクトル [m]
  * `set_torque::StaticArraysCore.MVector{4, Float32}`: トルク設定、ウインチ1..4 [Nm]
  * `set_speed::StaticArraysCore.MVector{4, Float32}`: 速度設定、ウインチ1..4 [m/s]
  * `set_force::StaticArraysCore.MVector{4, Float32}`: 力設定、ウインチ1..4 [N]
  * `roll::Float32`: ロール角 [rad]
  * `pitch::Float32`: ピッチ角 [rad]
  * `yaw::Float32`: ヨー角 [rad]
  * `var_01::Float32`: 一般変数01
  * `var_02::Float32`: 一般変数02
  * `var_03::Float32`: 一般変数03
  * `var_04::Float32`: 一般変数04
  * `var_05::Float32`: 一般変数05
  * `var_06::Float32`: 一般変数06
  * `var_07::Float32`: 一般変数07
  * `var_08::Float32`: 一般変数08
  * `var_09::Float32`: 一般変数09
  * `var_10::Float32`: 一般変数10
  * `var_11::Float32`: 一般変数11
  * `var_12::Float32`: 一般変数12
  * `var_13::Float32`: 一般変数13
  * `var_14::Float32`: 一般変数14
  * `var_15::Float32`: 一般変数15
  * `var_16::Float32`: 一般変数16
