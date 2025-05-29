すべての診断変数。

  * `trunc::Int64`: スペクトル解像度: 球面調和関数の最大次数 (0ベース)
  * `nlat_half::Int64`: グリッド解像度: 一つの半球の緯度リングの数 (赤道を含む)
  * `nlayers::Int64`: 垂直層の数
  * `nparticles::Int64`: 粒子輸送のための粒子の数
  * `tendencies::SpeedyWeather.Tendencies`: 予測変数の傾向 (スペクトルおよびグリッド)
  * `grid::SpeedyWeather.GridVariables`: グリッド化された予測変数
  * `dynamics::SpeedyWeather.DynamicsVariables`: 力学コアのための中間変数
  * `physics::SpeedyWeather.PhysicsVariables`: 物理パラメータ化から返されるグローバルフィールド
  * `particles::SpeedyWeather.ParticleVariables{NF, ArrayType, ParticleVector, VectorType, Grid} where {NF, ArrayType, Grid, ParticleVector, VectorType}`: 粒子輸送のための中間変数
  * `column::SpeedyWeather.ColumnVariables`: 物理パラメータ化のための垂直カラム
  * `temp_average::Any`: 各水平層の平均温度 [K]
  * `scale::Base.RefValue`: 渦度と発散に適用されるスケール
