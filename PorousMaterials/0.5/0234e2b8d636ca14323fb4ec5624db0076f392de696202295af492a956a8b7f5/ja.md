データ構造は、単位セルボックス（`Box`）上に重ねられたポイントの正規の[各座標間の等間隔]グリッドを表します。各グリッドポイントには、型`T`のデータ`data`が関連付けられ、3D配列に格納されています。

# 属性

  * `box::Box`: グリッドポイントが重ねられるブラバイス格子を説明します。すべての面のグリッドポイントが含まれます。
  * `n_pts::Tuple{Int, Int, Int}`: x、y、z方向のグリッドポイントの数。0および1の分数座標が含まれます。
  * `data::Array{T, 3}`: 各グリッドポイントに関連付けられたデータを含む三次元配列。
  * `units::Symbol`: 各データポイントに関連付けられた単位。
  * `origin::Array{Float64, 1}`: グリッドの原点。
