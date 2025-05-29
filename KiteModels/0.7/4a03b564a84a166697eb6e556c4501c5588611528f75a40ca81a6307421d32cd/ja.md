```
mutable struct KPS3{S, T, P} <: AbstractKiteModel
```

カイトパワーシステムの状態。パラメータ：

  * S: スカラー型、例：SimFloat ドキュメントではAnyとして言及されていますが、このモジュールで使用されるときは常にSimFloatであり、Anyではありません。
  * T: ベクトル型、例：MVector{3, SimFloat}
  * P: システムのポイント数、セグメント+1

通常、このパッケージのユーザーはこの型のメンバーに直接アクセスする必要はなく、代わりに入力および出力関数を使用してください。

  * `set::KiteUtils.Settings`: 設定構造体への参照
  * `kcu::KitePodModels.KCU`: KCUモデルへの参照（KitePodModelsパッケージで実装されたカイト制御ユニット）
  * `am::AtmosphericModels.AtmosphericModel`: 大気モデルへの参照（AtmosphericModelsパッケージで実装された） デフォルト: AtmosphericModel()
  * `wm::Union{Nothing, WinchModels.AbstractWinchModel}`: ウインチモデルへの参照（WinchModelsパッケージで実装された） デフォルト: nothing
  * `iter::Int64`: イテレーション、関数residual!への呼び出し回数 デフォルト: 0
  * `calc_cl::Dierckx.Spline1D`: 提供された値のペアに基づいてリフト係数を計算するための関数。
  * `calc_cd::Dierckx.Spline1D`: 提供された値のペアに基づいて抗力係数を計算するための関数。
  * `v_wind::Any`: カイトの高さでの風ベクトル デフォルト: zeros(S, 3)
  * `v_wind_gnd::Any`: 基準高さでの風ベクトル デフォルト: zeros(S, 3)
  * `v_wind_tether::Any`: テザーの抗力計算に使用される風ベクトル デフォルト: zeros(S, 3)
  * `v_apparent::Any`: カイトの見かけの風ベクトル デフォルト: zeros(S, 3)
  * `v_app_perp::Any`: v*apparentに垂直なベクトル; calc*dragの出力 デフォルト: zeros(S, 3)
  * `alpha_2::Any`: カイトの迎角; set*cl*cd!の出力 デフォルト: 0.0
  * `drag_force::Any`: カイトとブライドルの抗力; calc*aero*forcesの出力 デフォルト: zeros(S, 3)
  * `lift_force::Any`: カイトの揚力; calc*aero*forcesの出力 デフォルト: zeros(S, 3)
  * `steering_force::Any`: カイトに作用する操舵力; calc*aero*forcesの出力 デフォルト: zeros(S, 3)
  * `last_force::Any`: デフォルト: zeros(S, 3)
  * `spring_force::Any`: 現在のテザーセグメントのばね力、calc_resの出力 デフォルト: zeros(S, 3)
  * `total_forces::Any`: デフォルト: zeros(S, 3)
  * `force::Any`: 現在のセグメントに作用するばね力と抗力の合計、calc_resの出力 デフォルト: zeros(S, 3)
  * `unit_vector::Any`: 現在のテザーセグメントの方向の単位ベクトル、calc_resの出力 デフォルト: zeros(S, 3)
  * `av_vel::Any`: 現在のテザーセグメントの平均速度、calc_resの出力 デフォルト: zeros(S, 3)
  * `kite_y::Any`: カイトの固定参照フレームのyベクトル、calc*aero*forcesの出力 デフォルト: zeros(S, 3)
  * `segment::Any`: 1つのテザーセグメントを表すベクトル（p1-p2） デフォルト: zeros(S, 3)
  * `last_tether_drag::Any`: 最後に計算されたテザーセグメントの抗力ベクトル デフォルト: zeros(S, 3)
  * `vec_z::Any`: カイト参照フレームのzベクトル デフォルト: zeros(S, 3)
  * `res1::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: 残差の部分1、pos'とvelの違い、非平坦、主に単体テスト用 デフォルト: zeros(SVector{P, KVec3})
  * `res2::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: 残差の部分2、vel'とaccの違い、非平坦、主に単体テスト用 デフォルト: zeros(SVector{P, KVec3})
  * `pos::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: 粒子の位置のベクトル デフォルト: zeros(SVector{P, KVec3})
  * `vel_kite::Any`: カイトの速度ベクトル デフォルト: zeros(S, 3)
  * `seg_area::Any`: 1つのテザーセグメントの面積 [m²] デフォルト: zero(S)
  * `bridle_area::Any`: 実際のブライドル面積の合計 [m²] デフォルト: zero(S)
  * `c_spring::Any`: ばね定数、テザーセグメントの長さに依存 デフォルト: zero(S)
  * `segment_length::Any`: ストレスのないセグメントの長さ [m] デフォルト: 0.0
  * `damping::Any`: 減衰係数、テザーセグメントの長さに依存 デフォルト: zero(S)
  * `last_v_app_norm_tether::Any`: テザーセグメントでの見かけの風速の最後のノルム [m/s] デフォルト: zero(S)
  * `param_cl::Any`: カイトの揚力係数、迎角に依存 デフォルト: 0.2
  * `param_cd::Any`: カイトの抗力係数、迎角に依存 デフォルト: 1.0
  * `cor_steering::Any`: 操舵のための補正項、論文ではi_(s,c)と呼ばれ、式30 デフォルト: zero(S)
  * `psi::Any`: ラジアンでの方位角; 初期値はゼロ デフォルト: zero(S)
  * `beta::Any`: ラジアンでの仰角; 初期値は約70度 デフォルト: deg2rad((se()).elevation)
  * `alpha_depower::Any`: デパワー角 [deg] デフォルト: 0.0
  * `t_0::Any`: 現在の時間間隔の相対開始時間 デフォルト: 0.0
  * `v_reel_out::Any`: ウインチの巻き出し速度 [m/s] デフォルト: 0.0
  * `last_v_reel_out::Any`: 最後の時間ステップ中の巻き出し速度 デフォルト: 0.0
  * `l_tether::Any`: 伸びていないテザーの長さ デフォルト: 0.0
  * `rho::Any`: カイトの高さでの空気密度 デフォルト: 0.0
  * `depower::Any`: 実際の相対デパワー設定、0 .. 1.0の間でなければならない デフォルト: 0.0
  * `steering::Any`: 実際の相対操舵設定、-1.0 .. 1.0の間でなければならない デフォルト: 0.0
  * `kcu_steering::Any`: kcu後の操舵、オフセットとデパワー感度を適用する前、-1.0 .. 1.0 デフォルト: 0.0
  * `stiffness_factor::Any`: テザーの剛性のための係数、最初に低剛性で定常状態を見つけるために使用 デフォルト: 1.0
  * `initial_masses::StaticArraysCore.MVector{P, S} where {S, P}`: 点質量の初期質量 デフォルト: ones(P)
  * `masses::StaticArraysCore.MVector{P, S} where {S, P}`: 現在の質量、テザーの全長に依存 デフォルト: ones(P)
  * `forces::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: 粒子に作用する力のベクトル デフォルト: zeros(SVector{P, KVec3})
  * `sync_speed::Union{Nothing, S} where S`: モーター/発電機の同期速度 デフォルト: 0.0
  * `set_torque::Union{Nothing, S} where S`: モーター/発電機のset_torque デフォルト: nothing
