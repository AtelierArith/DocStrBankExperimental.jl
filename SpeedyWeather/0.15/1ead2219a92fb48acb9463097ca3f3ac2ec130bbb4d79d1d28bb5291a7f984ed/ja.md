地球の地形をファイルから読み込み、平滑化します。

  * `path::String`: 地形ファイルを含むフォルダへのパス、パッケージパスのデフォルト
  * `file::String`: 地形のファイル名
  * `file_Grid::Type{<:SpeedyWeather.RingGrids.AbstractGrid}`: 地形ファイルが存在するグリッド
  * `scale::Any`: 地形を因子でスケール
  * `smoothing::Bool`: 地形フィールドを平滑化しますか？
  * `smoothing_power::Any`: 平滑化のためのラプラシアンの指数
  * `smoothing_strength::Any`: 最高次数 l に掛けられる値
  * `smoothing_fraction::Any`: 平滑化する最高波数の割合
  * `orography::Any`: グリッドポイント空間での高さ [m]。
  * `geopot_surf::Any`: 表面の重力ポテンシャル、高さ*重力 [m²/s²]
