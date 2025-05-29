パラメータ構造体を次のオプションとデフォルト値で作成します     T=Float32                 # 数値形式

```
Tprog=T                   # 予測変数の数値形式
Tcomm=Tprog               # ゴーストポイントコピーの数値形式
Tini=Tprog                # 初期条件の精度を下げるための数値形式

# ドメイン解像度と比率
nx::Int=100                         # x方向のグリッドセル数
Lx::Float64=4000e3                  # x方向のドメインの長さ [m]
L_ratio::Float64=2                  # Lx/Lyのドメインアスペクト比

# 物理定数
g::Float64 = 0.1                    # 重力加速度 [m/s]
H::Float64 = 500.                   # 静止時の層の厚さ [m]
ρ::Float64 = 1e3                    # 水の密度 [kg/m^3]
ϕ::Float64 = 45.                    # ドメインの中央緯度（コリオリ用） [°]
ω::Float64 = 2π/(24*3600)           # 地球の角周波数 [s^-1]
R::Float64 = 6.371e6                # 地球の半径 [m]

# スケール
scale::Float64=2^6                  # 運動方程式u,vのための乗法スケール
scale_sst::Float64=2^15             # sstのための乗法スケール

# 風強制オプション
wind_forcing_x::String="shear"      # "channel", "double_gyre", "shear","constant" または "none"
wind_forcing_y::String="constant"   # "channel", "double_gyre", "shear","constant" または "none"
Fx0::Float64=0.12                   # x方向の風応力強度 [Pa]
Fy0::Float64=0.0                    # y方向の風応力強度 [Pa]
seasonal_wind_x::Bool=true          # 風応力を周波数ωFx,ωFyの正弦で変化させる
seasonal_wind_y::Bool=false         # y成分についても同様
ωFx::Float64=2                      # x成分の周波数 [1/year]
ωFy::Float64=2                      # y成分の周波数 [1/year]

# 底部地形オプション
topography::String="ridges"         # "ridge", "seamount", "flat", "ridges", "bathtub"
topo_ridges_positions::Vector{Float64} = [0.05,0.25,0.45,0.9]
topo_height::Float64 = 100.         # 海山の高さ [m]
topo_width::Float64 = 300e3         # 海山の水平スケール [m]

# 表面緩和
surface_relax::Bool=false           # はい？
t_relax::Float64 = 100.             # 緩和の時間スケール [日]
η_refh::Float64 = 5.                # インターフェース緩和プロファイルの高さ差 [m]
η_refw::Float64 = 50e3              # インターフェース緩和に使用される接線の幅 [m]

# 表面強制
surface_forcing::Bool=false         # はい？
ωFη::Float64 = 1.0                  # 表面強制の周波数 [1/year]
A::Float64 = 3e-5                   # 振幅 [m/s]
ϕk::Float64 = ϕ                     # ケルビン波ポンピングの中央緯度
wk::Float64 = 10e3                  # 表面強制に使用されるガウスの幅 [m]

# 時間ステッピングオプション
time_scheme::String="RK"            # ルンゲ・クッタ（"RK"）または強安定性保存RK
                                    # "SSPRK2","SSPRK3","4SSPRK3"
RKo::Int=4                          # RK時間ステッピングスキームの次数（2, 3または4）
RKs::Int=3                          # SSPRK2のステージ数
RKn::Int=5                          # n^2 = s = SSPRK3のステージ数
cfl::Float64 = 0.9                  # CFL数（RK4には1.0、RK3には0.6を推奨）
Ndays::Float64 = 200.0              # 統合する日数
nstep_diff::Int=1                   # nstep_diff時間ステップごとの拡散部分。
nstep_advcor::Int=0                 # nstep_advcor時間ステップごとの対流とコリオリの更新。
                                    # 0はすべてのRK4サブステップに含まれることを意味します
compensated::Bool=false             # 時間積分における補償和算？

# 境界条件オプション
bc::String="periodic"               # "periodic" または非周期的な場合は他の何か
α::Float64 = 2                      # 側面境界条件パラメータ
                                    # 0は自由滑り、0<α<2は部分滑り、2は滑りなし

# アジョイント法のためのパラメータ
data_steps::StepRange{Int,Int} = 0:1:0      # データが存在する時間ステップ
data::Array{Float32, 1} = [0.]              # モデルデータ
J::Float64 = 0.                             # コスト関数評価のためのプレースホルダー
j::Int = 1                                  # データ内のエントリを追跡するため

# チェックポイント変数
i::Int = 0                                  # 現在の時間ステップのプレースホルダー、Checkpointing.jlに必要

# 運動量対流オプション
adv_scheme::String="ArakawaHsu"     # "Sadourny" または "ArakawaHsu"
dynamics::String="nonlinear"        # "linear" または "nonlinear"

# 底部摩擦オプション
bottom_drag::String="none"          # "linear", "quadratic" または "none"
cD::Float64 = 1e-5                  # 二次のための底部摩擦係数 [無次元]
τD::Float64 = 300.                  # 線形のための底部摩擦係数 [日]

# 拡散オプション
diffusion::String="constant"        # "Smagorinsky" または "constant"、両方の場合でバイハーモニック
νB::Float64 = 500.0                 # [m^2/s] 定数バイハーモニック拡散のためのスケーリング定数
cSmag::Float64 = 0.15               # スマゴリンシー係数 [無次元]

# トレーサー対流
tracer_advection::Bool=true         # はい？
tracer_relaxation::Bool=true        # はい？
tracer_consumption::Bool=false      # いいえ？
sst_initial::String="waves"         # "west", "south", "linear", "waves","rect", "flat" または "restart"
sst_rect_coords::Array{Float64,1}=[0.,0.15,0.,1.0]
                                    # (x0,x1,y0,y1)は[0,1]内の長方形のサイズ
Uadv::Float64 = 0.2                 # トレーサー対流のための速度スケール [m/s]
SSTmax::Float64 = 1.                # トレーサー（海面温度）の初期条件の最大値
SSTmin::Float64 = -1.               # トレーサー（海面温度）の初期条件の最小値
τSST::Float64 = 100                 # トレーサー復元時間スケール [日]
jSST::Float64 = 365                 # トレーサー消費 [日]
SSTw::Float64 = 5e5                 # ICおよびインターフェース緩和に使用される接線の幅 [m]
SSTϕ::Float64 = 0.5                 # sstエッジの緯度/経度の割合 ∈ [0,1]
SSTwaves_ny::Float64 = 4            # y方向の波の頂点/谷
SSTwaves_nx::Float64 = SSTwaves_ny*L_ratio  # x方向の波の頂点/谷
SSTwaves_p::Float64 = 1/2           # 長方形のための指数（p<1）/波の滑らかさ（p>=1）

# 出力オプション
output::Bool=false                  # netcdf出力？
output_vars::Array{String,1}=["u","v","η","sst"]  # 出力する変数は？ "du","dv","dη","H","ζ" も許可されている
output_dt::Float64 = 24             # 出力時間ステップ [時間]
outpath::String=pwd()               # 出力フォルダへのパス
compression_level::Int=3            # 圧縮レベル
return_time::Bool=false             # 予測変数のシミュレーション時間を返す？

# 初期条件
initial_cond::String="rest"         # "rest" またはファイルからの再起動のための "ncfile"
initpath::String=outpath            # 再起動ファイルを取得するフォルダ
init_run_id::Int=0                  # 再起動のための実行ID
init_starti::Int=-1                 # 開始する時間ステップ（-1は最後を意味する）
get_id_mode::String="continue"      # 実行IDを決定する方法："continue" または "fill"
run_id::Int=-1                      # 特定の実行IDで出力
init_interpolation::Bool=true       # グリッドが一致しない場合に初期条件を補間しますか？
```
