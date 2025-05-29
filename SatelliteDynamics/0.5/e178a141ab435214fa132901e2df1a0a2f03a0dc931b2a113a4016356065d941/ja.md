ジオセントリック位置を同等の地球固定位置に変換します。

引数:

  * `geoc::AbstractArray{<:Real, 1}`: ジオセントリック座標 (経度, 緯度, 高度) [ラジアン] / [度]
  * `use_degrees:Bool`: `true` の場合、入力を度として解釈します。

戻り値:

  * `ecef::AbstractArray{<:Real, 1}`: 地球固定座標 [m]
