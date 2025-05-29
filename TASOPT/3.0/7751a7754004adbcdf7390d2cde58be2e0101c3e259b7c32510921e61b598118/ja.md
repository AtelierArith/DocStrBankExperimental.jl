```julia
mutable struct fuselage_tank
```

胴体タンクコンポーネント。通常は水素航空機用

  * `fueltype::String`: 燃料タイプ名
  * `tank_count::Int64`: 燃料タンクの数
  * `placement::String`: 燃料タンクの位置
  * `sizes_insulation::Bool`: 断熱材のサイズ設定フラグ
  * `Wfuelintank::Float64`: 一つのタンク内の燃料の重さ (N)
  * `clearance_fuse::Float64`
  * `t_insul::Vector{Float64}`: 断熱層の厚さのベクトル (m)
  * `material_insul::Vector{TASOPT.materials.ThermalInsulator}`: 断熱材のベクトル
  * `iinsuldes::Vector{Int64}`: 断熱層設計インデックスのベクトル
  * `inner_material::TASOPT.materials.StructuralAlloy`: 内部容器の材料
  * `outer_material::TASOPT.materials.StructuralAlloy`: 外部容器の材料
  * `ARtank::Float64`: タンクヘッドのアスペクト比
  * `theta_inner::Float64`: 内部容器の補強材の角度位置
  * `theta_outer::Vector{Float64}`: 外部容器の補強材の角度位置のベクトル
  * `Ninterm::Float64`: 外部容器の中間補強材の数
  * `pvent::Float64`: 排気圧 (Pa)
  * `pinitial::Float64`: 充填圧 (Pa)
  * `pmin::Float64`: 最小許容タンク圧 (Pa)
  * `t_hold_orig::Float64`: 出発保持時間 (s)
  * `t_hold_dest::Float64`: 到着保持時間 (s)
  * `TSLtank::Float64`: タンク設計に使用される海面温度 (K)
  * `rhofuel::Float64`: 液体燃料の密度 (kg/m^3)
  * `Tfuel::Float64`: タンク内の液体燃料の温度 (K)
  * `rhofuelgas::Float64`: ガス燃料の密度 (kg/m^3)
  * `hvap::Float64`: 燃料の蒸発の比エンタルピー (J/kg)
  * `boiloff_rate::Float64`: 巡航開始時のタンクのボイルオフ率 (%/h)
  * `ftankadd::Float64`: 容器の追加質量比
  * `ew::Float64`: 容器の溶接効率
  * `ullage_frac::Float64`: 最小アラッジフラクション
  * `qfac::Float64`: 熱漏れ係数
  * `pfac::Float64`: 圧力上昇係数
