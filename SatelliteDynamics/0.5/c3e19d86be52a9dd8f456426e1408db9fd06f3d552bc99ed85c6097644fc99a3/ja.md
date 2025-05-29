地球固定フレームのトポセントリックフレームにおける物体の座標を計算します。

引数:

  * `station_ecef::AbstractArray{<:Real, 1}`: 地球固定のカートesianステーション座標
  * `ecef::AbstractArray{<:Real, 1}`: 地球固定ステーションにおける物体の座標
  * `conversion::Bool`: 使用する変換タイプ。 "geocentric" または "geodetic"

戻り値:

  * `E::AbstractArray{Float64, 2}`: トポセントリック回転行列
