地理座標を地球固定位置に変換

引数:

  * `ecef::AbstractArray{<:Real, 1}`: 地球固定位置 [m]
  * `use_degrees:Bool`: `true` の場合、結果を度単位で返します

戻り値:

  * `geod::AbstractArray{<:Real, 1}`: 地心座標 (経度、緯度、高度) [rad] / [deg]
