```
設定
```

フラット構造体で、シミュレーターとビューワーの設定を定義します。

  * `sim_settings::String`: 設定のyamlファイルの名前 デフォルト:
  * `log_file::String`: 拡張子なしのファイル名  [再生のみ] デフォルト:
  * `log_level::Float64`: コンソールに表示するメッセージの数、0=なし デフォルト: 2
  * `time_lapse::Float64`: 相対再生速度 デフォルト: 0
  * `sim_time::Float64`: シミュレーション時間             [シミュレーションのみ] デフォルト: 0
  * `segments::Int64`: テザーセグメントの数 デフォルト: 0
  * `sample_freq::Int64`: サンプリング周波数（Hz） デフォルト: 0
  * `zoom::Float64`: システムビューのズームファクター デフォルト: 0
  * `kite_scale::Float64`: 4点カイトの相対ズームファクター デフォルト: 1.0
  * `fixed_font::String`: 代替の固定ピッチフォントの名前またはファイルパス+ファイル名 デフォルト:
  * `l_tether::Float64`: 初期テザー長       [m] デフォルト: 0
  * `elevation::Float64`: 初期高度角                [度] デフォルト: 0
  * `v_reel_out::Float64`: 初期リールアウト速度    [m/s] デフォルト: 0
  * `depower::Float64`: 初期デパワー設定    [%] デフォルト: 0
  * `abs_tol::Float64`: DAEソルバーの絶対許容誤差 [m, m/s] デフォルト: 0.0
  * `rel_tol::Float64`: DAEソルバーの相対許容誤差 [-] デフォルト: 0.0
  * `solver::String`: DAEソルバー、IDAまたはDFBDFのいずれか デフォルト: DFBDF
  * `linear_solver::String`: GMRESまたはDenseのいずれか デフォルト: GMRES
  * `max_order::Int64`: 最大次数、通常は3から5の間 デフォルト: 4
  * `max_iter::Int64`: 定常状態ソルバーの最大反復回数 デフォルト: 1
  * `c0::Float64`: ステアリングオフセット   -0.0032           [-] デフォルト: 0
  * `c_s::Float64`: ステアリング係数1点モデル デフォルト: 0
  * `c2_cor::Float64`: 補正係数1点モデル デフォルト: 0
  * `k_ds::Float64`: ステアリング感度に対するデパワー角の影響 デフォルト: 0
  * `delta_st::Float64`: ステアリング増分（右を押したとき） デフォルト: 0
  * `max_steering::Float64`: 4点モデルのサイドプレーンの最大ステアリング角 [度] デフォルト: 0
  * `cs_4p::Float64`: 4点モデルのステアリング感度の補正係数 デフォルト: 1.0
  * `alpha_d_max::Float64`: 最大デパワー角              [度] デフォルト: 0
  * `depower_offset::Float64`: rel_depower=0.236のとき、カイトは完全にパワーを持つ [%] デフォルト: 23.6
  * `model::String`: ビューワー用のカイトの3Dモデルのファイル名 デフォルト: data/kite.obj
  * `physical_model::String`: フォイル形状の拡張子の有無にかかわらずのファイル名 [dat形式] デフォルト:
  * `version::Int64`: 使用するモデルのバージョン デフォルト: 1
  * `mass::Float64`: センサーユニットを含むカイトの質量     [kg] デフォルト: 0
  * `area::Float64`: 投影されたカイトの面積            [m^2] デフォルト: 0
  * `rel_side_area::Float64`: 相対サイドエリア               [%] デフォルト: 0
  * `height_k::Float64`: カイトの高さ               [m] デフォルト: 0
  * `alpha_cl::Vector{Float64}`: デフォルト: []
  * `cl_list::Vector{Float64}`: デフォルト: []
  * `alpha_cd::Vector{Float64}`: デフォルト: []
  * `cd_list::Vector{Float64}`: デフォルト: []
  * `cms::Float64`: ステアリング依存モーメント係数 デフォルト: 0
  * `width::Float64`: カイトの幅                [m] デフォルト: 0
  * `alpha_zero::Float64`: 5であるべき                      [度] デフォルト: 0
  * `alpha_ztip::Float64`: デフォルト: 0
  * `m_k::Float64`: 相対ノーズ距離; m_kを増加させるとターンレート法のC2が増加 デフォルト: 0
  * `rel_nose_mass::Float64`: デフォルト: 0
  * `rel_top_mass::Float64`: 上部粒子の質量は上部と側面の粒子の合計に対する相対値 デフォルト: 0
  * `smc::Float64`: ステアリングモーメント係数 デフォルト: 0
  * `cmq::Float64`: ピッチレート依存モーメント係数 デフォルト: 0
  * `cord_length::Float64`: カイトの平均空力コード長 [m] デフォルト: 0
  * `c_spring_kite::Float64`: カイトスプリングの単位スプリング定数係数 [N] デフォルト: 0
  * `damping_kite_springs::Float64`: カイトスプリングの単位ダンピング係数 [Ns] デフォルト: 0
  * `rel_mass_p2::Float64`: p2の相対質量 デフォルト: 0
  * `rel_mass_p3::Float64`: p3の相対質量 デフォルト: 0
  * `rel_mass_p4::Float64`: p4およびp5の相対質量 デフォルト: 0
  * `foil_file::String`: フォイル形状のファイル名 [dat形式] デフォルト: data/ram*air*kite_foil.dat
  * `top_bridle_points::Vector{Vector{Float64}}`: CADフレーム内のカイト本体にない上部ブライドルポイント デフォルト: [[0.290199, 0.784697, -2.61305], [0.392683, 0.785271, -2.61201], [0.498202, 0.786175, -2.62148], [0.535543, 0.786175, -2.62148]]
  * `bridle_tether_diameter::Float64`: ブライドルテザーの直径 [mm] デフォルト: 2.0
  * `power_tether_diameter::Float64`: パワーテザーの直径 [mm] デフォルト: 2.0
  * `steering_tether_diameter::Float64`: ステアリングテザーの直径 [mm] デフォルト: 1.0
  * `crease_frac::Float64`: 後縁変形のひだのための正規化されたフォイルコードに沿った距離 デフォルト: 0.82
  * `bridle_fracs::Vector{Float64}`: ブライドル取り付けポイントのための正規化されたフォイルコードに沿った距離 デフォルト: [0.088, 0.31, 0.58, 0.93]
  * `fixed_index::Int64`: カイトがねじれる周りのブライドルフラクションインデックス デフォルト: 1
  * `quasi_static::Bool`: 擬似静的テザー点を使用するかどうか デフォルト: false
  * `d_line::Float64`: ブライドルラインの直径                  [mm] デフォルト: 0
  * `h_bridle::Float64`: ブライドルの高さ                    [m] デフォルト: 0
  * `l_bridle::Float64`: ブライドルラインの長さの合計 [m] デフォルト: 0
  * `rel_compr_stiffness::Float64`: カイトスプリングの相対圧縮剛性 デフォルト: 0
  * `rel_damping::Float64`: カイトスプリングの相対ダンピング（メインテザーに対して） デフォルト: 0
  * `kcu_model::String`: カイト制御ユニットのモデル、KCU1またはKCU2 デフォルト: KCU1
  * `kcu_mass::Float64`: カイト制御ユニットの質量   [kg] デフォルト: 0
  * `kcu_diameter::Float64`: 抵抗計算のためのカイト制御ユニットの直径 [m] デフォルト: 0
  * `cd_kcu::Float64`: カイト制御ユニットの抗力係数 デフォルト: 0
  * `depower_zero::Float64`: alpha_zero = 0のためのデパワー設定 [%] デフォルト: 0
  * `degrees_per_percent_power::Float64`: 線形近似 [度/%] デフォルト: 0
  * `power2steer_dist::Float64`: パワーからステアリングラインまでの距離  [m] デフォルト: 0
  * `depower_drum_diameter::Float64`: デフォルト: 0
  * `tape_thickness::Float64`: デフォルト: 0
  * `v_depower::Float64`: デパワーの最大速度（単位/秒あたりのフルレンジ: 1単位） デフォルト: 0
  * `v_steering::Float64`: ステアリングの最大速度（単位/秒あたりのフルレンジ: 2単位） デフォルト: 0
  * `depower_gain::Float64`: 3.0は意味する: 33%以上の誤差 -> フルスピード デフォルト: 3.0
  * `steering_gain::Float64`: デフォルト: 3.0
  * `d_tether::Float64`: テザーの直径                 [mm] デフォルト: 0
  * `cd_tether::Float64`: テザーの抗力係数 デフォルト: 0
  * `damping::Float64`: 単位ダンピング係数        [Ns] デフォルト: 0
  * `c_spring::Float64`: 単位スプリング定数係数 [N] デフォルト: 0
  * `rho_tether::Float64`: ダイニーマの密度                   [kg/m³] デフォルト: 0
  * `e_tether::Float64`: テザーの軸方向引張弾性率     [Pa] デフォルト: 0
  * `winch_model::String`: ウインチモデル、AsyncMachineまたはTorqueControlledMachine デフォルト:
  * `max_force::Float64`: 最大（公称）テザー力; 短時間のオーバーロードが許可される [N] デフォルト: 4000
  * `v_ro_max::Float64`: 最大リールアウト速度                      [m/s] デフォルト: 8
  * `v_ro_min::Float64`: 最小リールアウト速度（=最大リールイン速度） [m/s] デフォルト: -8
  * `max_acc::Float64`: 最大加速度                       [m/s²] デフォルト: 0
  * `drum_radius::Float64`: ドラムの半径 [m] デフォルト: 0.1615
  * `gear_ratio::Float64`: ギアボックスの比率 デフォルト: 6.2
  * `inertia_total::Float64`: モーター、ギアボックス、ドラムの慣性、モーターから見た場合 [kgm²] デフォルト: 0
  * `f_coulomb::Float64`: コロンブ摩擦 [N] デフォルト: 122.0
  * `c_vf::Float64`: 粘性摩擦の係数 [Ns/m] デフォルト: 30.6
  * `p_speed::Float64`: スピードコントローラーの比例ゲイン デフォルト: 0
  * `i_speed::Float64`: スピードコントローラーの積分ゲイン デフォルト: 0
  * `v_wind::Float64`: 基準高さでの風速          [m/s] デフォルト: 0
  * `upwind_dir::Float64`: 初期上流方向                [度] デフォルト: 0
  * `temp_ref::Float64`: 基準高さでの温度         [°C] デフォルト: 0
  * `height_gnd::Float64`: 地上局の海面上の高さ  [m] デフォルト: 0
  * `h_ref::Float64`: 風速の基準高さ     [m] デフォルト: 0
  * `rho_0::Float64`: ゼロ高度および15 °Cでの空気密度    [kg/m³] デフォルト: 0
  * `alpha::Float64`: 風プロファイル法の指数 デフォルト: 0
  * `z0::Float64`: 表面粗さ                       [m] デフォルト: 0
  * `profile_law::Int64`: 1=EXP, 2=LOG, 3=EXPLOG, 4=FAST*EXP, 5=FAST*LOG, 6=FAST_EXPLOG デフォルト: 0
  * `use_turbulence::Float64`: Cabau, NLに対する乱流強度 デフォルト: 0
  * `v_wind_gnds::Vector{Float64}`: 乱流風場を計算するための基準高さでの風速 [m/s] デフォルト: []
  * `avg_height::Float64`: リールアウト中の平均高さ           [m] デフォルト: 0
  * `rel_turbs::Vector{Float64}`: v*wind*gndsでの相対乱流 デフォルト: []
  * `i_ref::Float64`: 15 m/sでの乱流強度の期待値 デフォルト: 0
  * `v_ref::Float64`: ハブ高さでの年間平均風速の5倍    [m/s] デフォルト: 0
  * `height_step::Float64`: z方向のグリッド解像度                                                 [m] デフォルト: 0
  * `grid_step::Float64`: xおよびy方向のグリッド解像度                                           [m] デフォルト: 0
