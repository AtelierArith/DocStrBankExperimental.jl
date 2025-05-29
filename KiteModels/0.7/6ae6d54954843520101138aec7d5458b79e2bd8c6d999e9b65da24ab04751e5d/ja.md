```
mutable struct RamAirKite{S, V, P} <: AbstractKiteModel
```

風力システムの状態、クォータニオンカイトモデルと地面への3本の操縦ラインを使用しています。パラメータ：

  * S: スカラー型、例：SimFloat ドキュメントではAnyとして言及されていますが、このモジュールで使用されるときは常にSimFloatであり、Anyではありません。
  * V: ベクトル型、例：KVec3
  * P: システムのテザー点の数、3セグメント+3

通常、このパッケージのユーザーはこの型のメンバーに直接アクセスする必要はなく、代わりに入力および出力関数を使用してください。

  * `set::KiteUtils.Settings`: 設定構造体への参照
  * `wing::VortexStepMethod.RamAirWing`: 幾何学的翼モデルへの参照
  * `aero::VortexStepMethod.BodyAerodynamics`: 空力翼モデルへの参照
  * `vsm_solver::VortexStepMethod.Solver`: VSM空力ソルバーへの参照
  * `point_system::KiteModels.PointMassSystem`: ポイント、セグメント、プーリー、テザーを持つ点質量システムへの参照
  * `am::AtmosphericModels.AtmosphericModel`: AtmosphericModelsパッケージに実装された大気モデルへの参照 デフォルト: AtmosphericModel()
  * `pos::Matrix`: テザー位置 デフォルト: zeros(S, 3, P)
  * `segment_lengths::Any`: 3本のテザーの非ストレスセグメント長 [m] デフォルト: zeros(S, 3)
  * `t_0::Any`: 現在の時間間隔の相対開始時間 デフォルト: 0.0
  * `tether_lengths::Any`: 非伸張テザー長 デフォルト: zeros(S, 3)
  * `rho::Any`: カイトの高さでの空気密度 デフォルト: 0.0
  * `masses::Any`: テザー質量 デフォルト: zeros(S, P)
  * `c_spring::Any`: 単位スプリング係数 デフォルト: zeros(S, 3)
  * `damping::Any`: 単位ダンピング係数 デフォルト: zeros(S, 3)
  * `torque_control::Bool`: スピード制御の代わりにトルク制御を使用するかどうか デフォルト: false
  * `e_x::Any`: カイト参照フレームのxベクトル デフォルト: zeros(S, 3)
  * `e_y::Any`: カイト参照フレームのyベクトル デフォルト: zeros(S, 3)
  * `e_z::Any`: カイト参照フレームのzベクトル デフォルト: zeros(S, 3)
  * `sys::Union{Nothing, ModelingToolkit.ODESystem}`: mtkモデルの簡略化されたシステム デフォルト: nothing
  * `vel_kite::Any`: カイトの速度 デフォルト: zeros(S, 3)
  * `I_b::Any`: ボディフレームのカイトx、y、z軸周りの慣性 デフォルト: zeros(S, 3)
  * `u0map::Union{Nothing, Array{Pair{Symbolics.Num, S}, 1}} where S`: カイト状態の初期化値 デフォルト: nothing
  * `p0map::Union{Nothing, Array{Pair{Symbolics.Num, S}, 1}} where S`: カイトパラメータの初期化値 デフォルト: nothing
  * `bridle_fracs::Any`: ブライドル取り付けの正規化された2Dフォイル上のX座標 デフォルト: [0.088, 0.31, 0.58, 0.93]
  * `crease_frac::Any`: デフォルト: 0.82
  * `top_bridle_points::Vector`: カイト上にない上部ブライドルポイント、CADフレーム内 デフォルト: [[0.290199, 0.784697, -2.61305], [0.392683, 0.785271, -2.61201], [0.498202, 0.786175, -2.62148], [0.535543, 0.786175, -2.62148]]
  * `bridle_tether_diameter::Float64`: ブライドルシステム内のテザーの直径 [mm] デフォルト: 2.0
  * `power_tether_diameter::Float64`: パワーテザーの直径 [mm] デフォルト: 2.0
  * `steering_tether_diameter::Float64`: 操縦テザーの直径 [mm] デフォルト: 1.0
  * `iter::Int64`: solve!呼び出しの数 デフォルト: 0
  * `unknowns_vec::Vector{Float64}`: デフォルト: zeros(SimFloat, 3)
  * `set_set_values::Function`: デフォルト: ()->begin         #= /home/terasaki/.julia/packages/KiteModels/fyU5V/src/ram*air*kite.jl:311 =#         nothing     end
  * `set_measure::Function`: デフォルト: ()->begin         #= /home/terasaki/.julia/packages/KiteModels/fyU5V/src/ram*air*kite.jl:312 =#         nothing     end
  * `set_vsm::Function`: デフォルト: ()->begin         #= /home/terasaki/.julia/packages/KiteModels/fyU5V/src/ram*air*kite.jl:313 =#         nothing     end
  * `set_unknowns::Function`: デフォルト: ()->begin         #= /home/terasaki/.julia/packages/KiteModels/fyU5V/src/ram*air*kite.jl:314 =#         nothing     end
  * `get_state::Function`: デフォルト: ()->begin         #= /home/terasaki/.julia/packages/KiteModels/fyU5V/src/ram*air*kite.jl:316 =#         nothing     end
  * `get_y::Function`: デフォルト: ()->begin         #= /home/terasaki/.julia/packages/KiteModels/fyU5V/src/ram*air*kite.jl:317 =#         nothing     end
  * `prob::Union{Nothing, SciMLBase.ODEProblem}`: デフォルト: nothing
  * `init_prob::Union{Nothing, SciMLBase.ODEProblem}`: デフォルト: nothing
  * `integrator::Union{Nothing, OrdinaryDiffEqCore.ODEIntegrator, Sundials.CVODEIntegrator}`: デフォルト: nothing
  * `init_integrator::Union{Nothing, OrdinaryDiffEqCore.ODEIntegrator, Sundials.CVODEIntegrator}`: デフォルト: nothing

```
