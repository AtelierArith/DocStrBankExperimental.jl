陸海マスク、分数、ファイルから読み込み。

  * `path::String`: 陸海マスクファイルを含むフォルダーへのパス、パッケージパスのデフォルト
  * `file::String`: 陸海マスクのファイル名
  * `file_Grid::Type{<:SpeedyWeather.RingGrids.AbstractGrid}`: 陸海マスクファイルが存在するグリッド
  * `mask::Any`: グリッドポイント空間上の陸海マスク [1]。陸=1、海=0、間の陸面積の割合。
