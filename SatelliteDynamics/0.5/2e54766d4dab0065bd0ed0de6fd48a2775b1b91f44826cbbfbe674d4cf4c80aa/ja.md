地球固定座標系から南東天頂座標系への回転行列を計算します。

引数:

  * `station_ecef::AbstractArray{<:Real, 1}`: 地球固定のデカルト座標のステーション座標
  * `conversion::Bool`: 使用する変換タイプ。 "geocentric" または "geodetic" のいずれか

戻り値:

  * `E::AbstractArray{Float64, 2}`: トポセントリック回転行列
