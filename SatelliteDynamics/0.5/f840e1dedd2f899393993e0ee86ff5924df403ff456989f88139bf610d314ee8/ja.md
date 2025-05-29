地球固定位置を地心位置に変換します。

引数:

  * `ecef::AbstractArray{<:Real, 1}`: 地球固定座標 [m]
  * `use_degrees:Bool`: `true` の場合、結果を度単位で返します

返り値:

  * `geoc`: 地心座標 (経度、緯度、高度) [rad] / [deg]
