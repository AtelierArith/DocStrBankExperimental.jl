水平スペクトル解像度と対応するグリッド、およびSpeedyWeather.jlの垂直座標を定義します。オプションは次のとおりです。

  * `NF::Type{<:AbstractFloat}`: [OPTION] モデル全体で使用される数値形式
  * `device::SpeedyWeather.AbstractDevice`: [OPTION] 実行するデバイスアーキテクチャ
  * `ArrayType::Type{<:AbstractArray}`: [OPTION] すべての変数に使用する配列タイプ
  * `VectorType::Type{<:AbstractVector}`: [DERIVED] ベクトルのタイプ
  * `MatrixType::Type{<:AbstractMatrix}`: [DERIVED] 行列のタイプ
  * `TensorType::Type{<:AbstractArray}`: [DERIVED] 3D配列のタイプ
  * `trunc::Int64`: [OPTION] 球面調和関数の最大次数としての水平解像度
  * `SpectralVariable2D::Type{<:AbstractArray}`: [DERIVED] 2Dのスペクトル変数のタイプ（水平のみ、1Dベクトルにフラット化）
  * `SpectralVariable3D::Type{<:AbstractArray}`: [DERIVED] 3Dのスペクトル変数のタイプ（水平のみ + 例：垂直、2D行列にフラット化）
  * `SpectralVariable4D::Type{<:AbstractArray}`: [DERIVED] 4Dのスペクトル変数のタイプ（水平のみ + 例：垂直と時間、3D配列にフラット化）
  * `Grid::Type{<:SpeedyWeather.RingGrids.AbstractGrid}`: [OPTION] グリッドポイント空間での計算に使用される水平グリッド
  * `GridVariable2D::Type{<:AbstractArray}`: [DERIVED] 2Dのグリッド変数のタイプ（水平のみ、1Dベクトルにフラット化）
  * `GridVariable3D::Type{<:AbstractArray}`: [DERIVED] 3Dのグリッド変数のタイプ（水平 + 例：垂直、2D行列にフラット化）
  * `GridVariable4D::Type{<:AbstractArray}`: [DERIVED] 4Dのグリッド変数のタイプ（水平 + 例：垂直 + 時間、3D配列にフラット化）
  * `dealiasing::Float64`: [OPTION] スペクトルとグリッド解像度を一致させる方法：ディーリアシングファクター、1=線形、2=二次、3=三次グリッド
  * `radius::Float64`: [OPTION] 球の半径 [m]
  * `nparticles::Int64`: [OPTION] 粒子輸送のための粒子の数 [1]
  * `ParticleVector::Type{<:AbstractArray}`: [DERIVED] 粒子ベクトルのArrayType
  * `nlat_half::Int64`: [DERIVED] 一つの半球の緯度リングの数（赤道を含む）
  * `nlat::Int64`: [DERIVED] 両半球の緯度リングの数
  * `npoints::Int64`: [DERIVED] 水平のグリッドポイントの総数
  * `nlayers::Int64`: [OPTION] 大気中の垂直層の数
  * `nlayers_soil::Int64`: [OPTION] 土壌/陸の垂直層の数

`nlat_half`と`npoints`は選択するべきではなく、`trunc`、`Grid`、および`dealiasing`から導出されます。
