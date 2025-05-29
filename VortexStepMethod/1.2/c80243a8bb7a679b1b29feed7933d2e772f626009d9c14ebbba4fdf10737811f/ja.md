```
RamAirWing <: AbstractWing
```

変形可能な空力表面を持つ曲線パラフォイルを表すラムエアウィングモデルです。

## コア機能

  * 3Dメッシュ（.objファイル）から派生した曲線翼ジオメトリ
  * 2D翼型データ（.datファイル）に基づく空力特性
  * 制御入力（ねじれ角と後縁変位）のサポート
  * 慣性および幾何学的特性の計算

## 注目すべきフィールド

  * `n_panels::Int16`: 空力メッシュ内のパネル数
  * `n_groups::Int16`: 分散変形のための制御グループ数
  * `mass::Float64`: 翼の総質量（kg）
  * `gamma_tip::Float64`: 中心から翼先端までの角度範囲
  * `inertia_tensor::Matrix{Float64}`: 凧のボディフレーム内の完全な3x3慣性テンソル
  * `T_cad_body::MVec3`: CADフレームからボディフレームへの変換ベクトル
  * `R_cad_body::MMat3`: CADフレームからボディフレームへの回転行列
  * `radius::Float64`: 翼の曲率半径
  * `theta_dist::Vector{Float64}`: パネルのねじれ角分布
  * `delta_dist::Vector{Float64}`: 後縁変位分布

使用の詳細については、コンストラクタ `RamAirWing(obj_path, dat_path; kwargs...)` を参照してください。
