東-北-天頂のトポセントリック状態を方位角、仰角、範囲に変換します。

引数:

  * `x::AbstractArray{<:Real, 1}`: 東-北-上の状態
  * `use_degrees:Bool`: `true` の場合、結果を度単位で返します

返り値:

  * `azel::AbstractArray{<:Real, 1}`: 方位角、仰角、範囲 [rad; rad; m]
