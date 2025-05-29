```
mutable struct KPS4{S, T, P, Q, SP} <: AbstractKiteModel
```

4点カイトモデルを使用したカイトパワーシステムの状態。パラメータ：

  * S: スカラー型、例：SimFloat ドキュメントではAnyとして言及されていますが、このモジュールで使用されるときは常にSimFloatであり、Anyではありません。
  * T: ベクトル型、例：MVector{3, SimFloat}
  * P: システムのポイント数、セグメント+1
  * Q: システム内のスプリングの数、P-1
  * SP: スプリングを説明する構造体

通常、このパッケージのユーザーはこの型のメンバーに直接アクセスする必要はなく、代わりに入力および出力関数を使用してください。

  * `set::KiteUtils.Settings`: 設定構造体への参照
  * `kcu::KitePodModels.KCU`: KCUモデルへの参照（KitePodModelsパッケージで実装されたカイトコントロールユニット）
  * `am::AtmosphericModels.AtmosphericModel`: AtmosphericModelsパッケージで実装された大気モデルへの参照 デフォルト: AtmosphericModel()
  * `wm::WinchModels.AbstractWinchModel`: WinchModelsパッケージで実装されたウインチモデルへの参照
  * `iter::Int64`: イテレーション、関数residual!への呼び出し回数 デフォルト: 0
  * `calc_cl::Dierckx.Spline1D`: 提供された値ペアに基づいてリフト係数を計算するための関数。
  * `calc_cd::Dierckx.Spline1D`: 提供された値ペアに基づいて抗力係数を計算するための関数。
  * `v_wind::Any`: カイトの高さでの風ベクトル デフォルト: zeros(S, 3)
  * `v_wind_gnd::Any`: 基準高さでの風ベクトル デフォルト: zeros(S, 3)
  * `v_wind_tether::Any`: テザーの抗力計算に使用される風ベクトル デフォルト: zeros(S, 3)
  * `v_apparent::Any`: カイトでの見かけの風ベクトル デフォルト: zeros(S, 3)
  * `bridle_factor::Any`: bridle*factor = set.l*bridle/bridle_length(set) デフォルト: 1.0
  * `side_cl::Any`: サイドリフト係数、左と右のリフト係数の差 デフォルト: 0.0
  * `drag_force::Any`: カイトとブライドルの抗力；calc*aero*forces!の出力 デフォルト: zeros(S, 3)
  * `side_force::Any`: カイトに作用するサイドフォース デフォルト: zeros(S, 3)
  * `f_d::Any`: デフォルト: zeros(S, 3)
  * `f_s::Any`: デフォルト: zeros(S, 3)
  * `ks::Any`: 最大操舵角（ラジアン） デフォルト: 0.0
  * `lift_force::Any`: カイトのリフトフォース；calc*aero*forces!の出力 デフォルト: zeros(S, 3)
  * `spring_force::Any`: 現在のテザーセグメントのスプリングフォース、calc*particle*forces!の出力 デフォルト: zeros(S, 3)
  * `last_force::Any`: 最後のウインチフォース デフォルト: zeros(S, 3)
  * `res1::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: デバッグおよび単体テスト用の残差1（pos,vel）のコピー デフォルト: zeros(SVector{P, KVec3})
  * `res2::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: デバッグおよび単体テスト用の残差2（vel,acc）のコピー デフォルト: zeros(SVector{P, KVec3})
  * `pos::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: ユーザーへの出力としての実際の位置のコピー デフォルト: zeros(SVector{P, KVec3})
  * `vel::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: ユーザーへの出力としての実際の速度のコピー デフォルト: zeros(SVector{P, KVec3})
  * `vel_kite::Any`: カイトの速度ベクトル デフォルト: zeros(S, 3)
  * `segment_length::Any`: ストレスのないセグメント長 [m] デフォルト: 0.0
  * `param_cl::Any`: カイトのリフト係数、迎角に依存 デフォルト: 0.2
  * `param_cd::Any`: カイトの抗力係数、迎角に依存 デフォルト: 1.0
  * `psi::Any`: 方位角（ラジアン）；初期値はゼロ デフォルト: zero(S)
  * `alpha_depower::Any`: デパワー角 [deg] デフォルト: 0.0
  * `pitch::Any`: ピッチ角 [rad] デフォルト: 0.0
  * `pitch_rate::Any`: ピッチレート [rad/s] デフォルト: 0.0
  * `alpha_2::Any`: 粒子Bでの迎角 デフォルト: 0.0
  * `alpha_3::Any`: 粒子Cでの迎角 デフォルト: 0.0
  * `alpha_4::Any`: 粒子Dでの迎角 デフォルト: 0.0
  * `side_slip::Any`: サイドスリップ角 [rad] デフォルト: 0.0
  * `t_0::Any`: 現在の時間間隔の相対開始時間 デフォルト: 0.0
  * `v_reel_out::Any`: ウインチの巻き出し速度 デフォルト: 0.0
  * `last_v_reel_out::Any`: 最後の時間ステップでの巻き出し速度 デフォルト: 0.0
  * `l_tether::Any`: 伸びていないテザーの長さ デフォルト: 0.0
  * `rho::Any`: カイトの高さでの空気密度 デフォルト: 0.0
  * `depower::Any`: 実際の相対デパワー設定、0 .. 1.0の間でなければならない デフォルト: 0.0
  * `steering::Any`: 実際の相対操舵設定、-1.0 .. 1.0の間でなければならない デフォルト: 0.0
  * `kcu_steering::Any`: kcu後の操舵、オフセットとデパワー感度を適用する前、-1.0 .. 1.0 デフォルト: 0.0
  * `stiffness_factor::Any`: テザーとブライドルの剛性の乗数 デフォルト: 1.0
  * `initial_masses::StaticArraysCore.MVector{P, S} where {S, P}`: 点質量の初期質量 デフォルト: ones(P)
  * `masses::StaticArraysCore.MVector{P, S} where {S, P}`: 現在の質量、テザーの全長に依存 デフォルト: zeros(P)
  * `springs::StaticArraysCore.MVector`: 構造体として定義されたスプリングのベクトル デフォルト: zeros(SP, Q)
  * `forces::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: 粒子に作用する力のベクトル デフォルト: zeros(SVector{P, KVec3})
  * `sync_speed::Union{Nothing, S} where S`: モーター/発電機の同期速度 デフォルト: 0.0
  * `set_torque::Union{Nothing, S} where S`: モーター/発電機のセットトルク デフォルト: nothing
  * `set_force::Union{Nothing, S} where S`: ウインチでの力のセット値、ログ用のみ デフォルト: nothing
  * `bearing::Union{Nothing, S} where S`: ログ用のみのベアリング角のセット値（ラジアン） デフォルト: nothing
  * `attractor::Union{Nothing, StaticArraysCore.SVector{2, S}} where S`: ログ用のみの引力点の座標 [方位角, 高度]（ラジアン） デフォルト: nothing
  * `x::Any`: カイト参照フレームのxベクトル デフォルト: zeros(S, 3)
  * `y::Any`: カイト参照フレームのyベクトル デフォルト: zeros(S, 3)
  * `z::Any`: カイト参照フレームのzベクトル デフォルト: zeros(S, 3)

```
