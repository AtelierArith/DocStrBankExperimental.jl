南東天頂トポセントリック状態を方位角、仰角、および距離に変換します。

引数:

  * `x::AbstractArray{<:Real, 1}`: 南東天頂状態
  * `use_degrees:Bool`: `true` の場合、結果を度単位で返します

返り値:

  * `azel::AbstractArray{<:Real, 1}`: 方位角、仰角、および距離 [rad; rad; m]
