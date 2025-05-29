地球固定から東北上座標基準への回転行列を計算します。

引数:

  * `station_ecef::AbstractArray{<:Real, 1}`: 地球固定のデカルト駅座標
  * `conversion::Bool`: 使用する変換タイプ。 "geocentric" または "geodetic" です。

返り値:

  * `E::AbstractArray{Real, 2}`: トポセントリック回転行列
